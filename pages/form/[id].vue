<script setup>
const supabase = useSupabaseClient()
const route = useRoute()
const cake = ref('')
const categories = ref([])
const sizes = ref([])
const form = ref({
    nama_pembeli: "",
    alamat_lengkap: "",
    no_hp: "",
    id_kue: 0,
})


const addData = async () => {
  const { error } = await supabase.from('customer').insert([form.value])
  if (!error) navigateTo('/form/submit')
  console.log(error)
}

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

onMounted (() => {
    getCakeId()
    getCategory()
    getSize()
})

</script>

<template>
    <div class="container-fluid pt-4">

        <div class="row">
            <div class="col-lg-1 text-end mt-2">
                <nuxt-link :to="`/catalogue/${cake.id}`" style="text-decoration: none; color: black;">
                    <i class="bi bi-arrow-left-circle fs-2"></i>
                </nuxt-link>
            </div>
            <div class="col-lg-10">
                <h2 class="mt-3">Isi data pemesanan</h2>
            </div>
        </div>

        <div class="row mt-5 justify-content-center">
            <div class="col-lg-5">
                <div class="card add rounded-4 shadow">
                    <div class="card-body">
                        <div class="row p-3">
                            <div class="col-md-4">
                                <img :src="cake?.foto_kue" alt="img-cake" class="img-cake rounded-4 mt-3">
                            </div>
                            <div class="col-md-7">
                                <ul>
                                    <li class="list-group-item name fw-semibold">{{ cake?.nama_kue }}</li>
                                    <li class="list-group-item">{{ cake?.kategori?.nama }}</li>
                                    <li class="list-group-item">Ukuran {{ cake?.ukuran?.nama }}</li>
                                    <li class="list-group-item">Free lilin</li>
                                    <li class="list-group-item price fw-bold">{{ cake?.harga }}</li>
                                </ul>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
            <div class="col-lg-4">
                <div class="card mb-5 rounded-4 shadow">
                    <div class="card-body">
                        <form @submit.prevent="addData" class="input-group p-3">
                            <div class="mb-3">
                                <label for="exampleFormControlInput1" class="form-label">Nama pemesan</label>
                                <input v-model="form.nama_pembeli" type="text" class="form-control" id="exampleFormControlInput1">
                            </div>
                            <div class="mb-3">
                                <label for="exampleFormControlInput1" class="form-label">Alamat</label>
                                <textarea v-model="form.alamat_lengkap" class="form-control" id="exampleFormControlInput1" aria-label="With textarea"></textarea>
                            </div>
                            <div class="mb-3">
                                <label for="exampleFormControlInput1" class="form-label">No Hp</label>
                                <input v-model="form.no_hp" type="text" class="form-control" id="exampleFormControlInput1">
                            </div>
                            <!-- <div class="mb-3">
                                <label for="exampleFormControlInput1" class="form-label">Nama kue</label>
                                <input type="text" class="form-control" id="exampleFormControlInput1">
                            </div> -->
                            <div class="text-end mt-3">
                                <button type="submit" class="btn rounded-5">Kirim</button>
                            </div>
                        </form>
                    </div>
                </div>
            </div>
        </div>

    </div>
</template>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Kavoon&family=Miltonian+Tattoo&family=Poppins:ital,wght@0,100;0,200;0,300;0,400;0,500;0,600;0,700;0,800;0,900;1,100;1,200;1,300;1,400;1,500;1,600;1,700;1,800;1,900&family=Red+Rose:wght@300..700&display=swap');


h2, h6, input, label, textarea, li, .btn {
    font-family: "Poppins", sans-serif;
}

input, textarea {
    width: 365px;
}

.btn{
    width: 100px;
    margin-left: 135px;
    color: white;
    background-color: #c6ac7b;
}

.add {
    height: 300px;
}

h6 {
    margin-top: 125px;
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

.img-cake {
    height: 200px;
}

.col-md-7 {
    margin-left: 15px;
}

</style>