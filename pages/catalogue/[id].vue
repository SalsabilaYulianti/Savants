<script setup>
const supabase = useSupabaseClient()
const route = useRoute()
const cake = ref('')
const categories = ref([])
const sizes = ref([])


const getCakeId = async () => {
    const { data, error } = await supabase.from('produk').select(`*, kategori(*), ukuran(*)`)
        .eq('id', route.params.id)
    if (data) {
        cake.value = data[0]
    }
}

const getCategory = async () => {
    const { data, error } = await supabase.from('kategori').select('*')
    if (data) categories.value = data
}

const getSize = async () => {
    const { data, error } = await supabase.from('ukuran').select('*')
    if (data) sizes.value = data
}

onMounted(() => {
    getCakeId()
    getCategory()
    getSize()
})
</script>

<template>
    <div class="container-fluid pt-4">

        <div class="row">
            <div class="col-lg-1 text-end mt-2">
                <nuxt-link to="/product" style="text-decoration: none; color: black;">
                    <i class="bi bi-arrow-left-circle fs-2"></i>
                </nuxt-link>
            </div>
            <div class="col-lg-10">
                <h2 class="mt-3">Detail</h2>
            </div>
        </div>

        <div class="row mt-5 justify-content-center">
            <div class="col-lg-3">
                <div class="card cake rounded-4 shadow">
                    <div class="card-body text-center p-3">
                        <img :src="cake.foto_kue" alt="img-cake">
                    </div>
                </div>
            </div>
            <div class="col-lg-5">
                <div class="card mb-5 rounded-4">
                    <div class="card-body">
                        <ul>
                            <li class="list-group-item name fw-semibold">{{ cake?.nama_kue }}</li>
                            <li class="list-group-item">{{ cake?.kategori?.nama }}</li>
                            <li class="list-group-item">Ukuran {{ cake?.ukuran?.nama }}</li>
                            <li class="list-group-item">Free lilin</li>
                            <li class="list-group-item price fw-bold">{{ cake?.harga }}</li>
                        </ul>
                        <div class="button mt-5">
                            <nuxt-link href="https://wa.me/6281224703915" style="text-decoration: none; color: black;">
                                <button class="btn pesan rounded-5 m-2">Pesan via Whatsapp</button>
                            </nuxt-link>
                            <nuxt-link :to="`/form/${cake.id}`">
                                <button class="btn btn-pesan rounded-5 m-2">Pesan sekarang</button>
                            </nuxt-link>
                        </div>
                    </div>
                </div>
            </div>
        </div>

    </div>
</template>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Kavoon&family=Miltonian+Tattoo&family=Poppins:ital,wght@0,100;0,200;0,300;0,400;0,500;0,600;0,700;0,800;0,900;1,100;1,200;1,300;1,400;1,500;1,600;1,700;1,800;1,900&family=Red+Rose:wght@300..700&display=swap');


h2,
h6,
li,
.btn {
    font-family: "Poppins", sans-serif;
}

.list-group-item {
    font-size: 20px;
    margin-top: 10px;
}

.name {
    font-size: 25px
}

.price {
    margin-top: 30px;
    font-size: 25px;
}

.cake {
    height: 390px;
}

h6 {
    margin-top: 125px;
}

.pesan {
    width: 225px;
    border: 3px solid #C6AC7B;
}

.btn-pesan {
    width: 200px;
    margin-left: 40px;
    color: white;
    font-weight: 500;
    background-color: #C6AC7B;
}

.button {
    margin-left: 20px
}

img {
    width: 280px;
    height: 350px;
}
</style>