<script setup>
const supabase = useSupabaseClient()
const categories = ref([])
const sizes = ref([])
const form = ref({
    nama_kue: "",
    id_kategori: "",
    id_ukuran: "",
    harga: "",
})

const addCake = async () => {
    const { error } = await supabase.from('produk').insert([form.value])
    if (!error) navigateTo('/product')
    console.log(error)
}

const getCategory = async () => {
    const { data, error } = await supabase.from('kategori').select('*')
    if (data) categories.value = data
}

const getSizes = async () => {
    const { data, error } = await supabase.from('ukuran').select('*')
    if (data) sizes.value = data
}


onMounted(() => {
    getCategory()
    getSizes()
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
                <h2 class="mt-3">Tambah Kue</h2>
            </div>
        </div>

        <div class="row mt-5 justify-content-center">
            <div class="col-lg-4">
                <div class="card add-img rounded-4 shadow">
                    <div class="card-body text-center">
                        <h6>Tambahkan foto kue disini</h6>
                    </div>
                </div>
            </div>
            <div class="col-lg-4">
                <div class="card mb-5 rounded-4 shadow">
                    <div class="card-body">
                        <form @submit.prevent="addCake" class="input-group p-3">
                            <div class="mb-3">
                                <label for="exampleFormControlInput1" class="form-label">Nama Kue</label>
                                <input v-model="form.nama_kue" type="text" class="form-control" id="exampleFormControlInput1">
                            </div>
                            <div class="mb-3 kategori">
                                <label for="kategori">Kategori</label>
                                <select v-model="form.id_kategori" class="form-control form-select" id="keperluan">
                                    <option v-for="(category, i) in categories" :key="i" :value="category.id">{{ category.nama }}</option>
                                </select>
                            </div>
                            <div class="mb-3 ukuran">
                                <label for="ukuran">Ukuran</label>
                                <select v-model="form.id_ukuran" class="form-control form-select" id="keperluan">
                                    <option v-for="(size, i) in sizes" :key="i" :value="size.id">{{ size.nama }}</option>
                                </select>                            
                            </div>
                            <div class="mb-3">
                                <label for="exampleFormControlInput1" class="form-label">Harga</label>
                                <input v-model="form.harga" type="text" class="form-control" id="exampleFormControlInput1">
                            </div>
                            <div class="text-end mt-3">
                                <button type="submit" class="btn rounded-5">Tambah</button>
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


h2, h6, input, label, .btn {
    font-family: "Poppins", sans-serif;
}

input {
    width: 365px;
}

.btn {
    width: 120px;
    margin-left: 125px;
    color: white;
    background-color: #C6AC7B;
}

.add-img {
    height: 300px;
}

h6 {
    margin-top: 125px;
}

.kategori, .ukuran {
    width: 100%;
}

</style>