<script setup>
const supabase = useSupabaseClient()
const keyword = ref('')
// const cakes = ref([])
const selectCake = ref({})
const categories = ref([])

function toggleDelete(cake) {
    selectCake.value = cake
}

const { data: cakes, refresh } = useLazyAsyncData('cakes', async () => {
    const { data, error } = await supabase.from('produk').select(`*, kategori(*)`)
        .ilike('nama_kue', `%${keyword.value}%`)
    return (data)
})

const getCategory = async () => {
    const { data, error } = await supabase.from('kategori').select('*')
    if (data) categories.value = data
}

const cakeFiltered = computed(() => {
    return cakes.value.filter((c) => {
        return (
            c.nama_kue?.toLowerCase().includes(keyword.value.toLowerCase()) ||
            c.kategori?.nama.toLowerCase().includes(keyword.value.toLowerCase())
        )
    })
})

const deleteCake = async (id) => {
    console.log(id)
    const { error } = await supabase.from('produk').delete().eq('id', id)
    if (error) throw error
    else
        refresh()
}

onMounted(() => {
    getCategory()
    refresh()
})
</script>

<template>
    <div class="container-fluid pt-4">

        <div class="row">
            <div class="col-lg-1 text-end mt-2">
                <nuxt-link to="/dashboard" style="text-decoration: none; color: black;">
                    <i class="bi bi-arrow-left-circle fs-2"></i>
                </nuxt-link>
            </div>
            <div class="col-lg-10">
                <h2 class="mt-3">Product</h2>
            </div>
        </div>

        <!--Search Categories and Add-->
        <div class="p-5">
            <div class="row p-2">
                <div class="col-lg-5">
                    <form @submit.prevent="getCake" class="input-group flex-nowrap">
                        <input v-model="keyword" type="text" class="form-control rounded-5" placeholder="Cari nama kue"
                            aria-label="Search" aria-describedby="search-addon" />
                    </form>
                </div>
                <div class="col-lg-2">
                    <select v-model="keyword" class="form-control form-select rounded-5" id="category">
                        <option value="">Category</option>
                        <option v-for="(category, i) in categories" :key="category.id" :value="category.nama">{{
                            category.nama }}</option>
                    </select>
                </div>
                <div class="col-lg-2"></div>
                <div class="col-lg-3 text-end">
                    <nuxt-link to="../product/add">
                        <button class="btn rounded-5 m-2">Tambah Kue</button>
                    </nuxt-link>
                </div>
            </div>
        </div>

        <!--Product-->
        <div class="p-5">
            <div class="card p-3 rounded shadow">
                <div v-for="(cake, i) in cakeFiltered" :key="i" class="card-body">
                    <div class="row p-3">
                        <div class="col-lg-2">
                            <img :src="cake.foto_kue" class="rounded-3" alt="img-cake">
                        </div>
                        <div class="col-lg-2">
                            <h5>{{ cake.nama_kue }}</h5>
                        </div>
                        <div class="col-lg-2">
                            <h5>{{ cake.harga }}</h5>
                        </div>
                        <div class="col-lg-2">
                            <h5>{{ cake.kategori.nama }}</h5>
                        </div>
                        <div class="col-lg-2">
                            <h5>{{ cake.ukuran?.nama }}</h5>
                        </div>
                        <div class="col-lg-1 text-end">
                            <i class="bi bi-pencil fs-3 fw-bold edit"></i>
                        </div>
                        <div class="col-lg-1">
                            <i class="bi bi-trash3 fs-3 fw-bold delete" data-bs-toggle="modal"
                                data-bs-target="#exampleModal" @click="toggleDelete(cake)"></i>
                        </div>
                    </div>
                    <hr>
                </div>
            </div>
        </div>


        <!-- Categories
        <div class="row categories mt-5 mx-5 justify-content-center">
            <div class="col-lg-2 text-center">
                <img src="~/assets/img/birthday-cake.png" alt="img-kategori">
                <h6 class="mt-2">Birthday cake</h6>
            </div>
            <div class="col-lg-2 text-center">
                <img src="~/assets/img/wedding-cake.png" alt="img-kategori">
                <h6 class="mt-2">Wedding cake</h6>
            </div>
            <div class="col-lg-2 text-center">
                <img src="~/assets/img/bolu-jadoel.png" alt="img-kategori">
                <h6 class="mt-2">Bolu jadoel</h6>
            </div>
            <div class="col-lg-2 text-center">
                <img src="~/assets/img/dessert.png" alt="img-kategori">
                <h6 class="mt-2">Dessert</h6>
            </div>
            <div class="col-lg-2 text-center">
                <img src="~/assets/img/custom.png" alt="img-kategori">
                <nuxt-link to="/custom" style="text-decoration: none;">
                    <h6 class="mt-2 custom rounded-5">Custom cake</h6>
                </nuxt-link>            
            </div>
        </div>

        Search
        <div class="row mt-5 d-flex justify-content-center">
            <div class="col-lg-6">
                <form class="input-group flex-nowrap">
                    <input type="text" class="form-control shadow rounded-5" placeholder="Cari nama atau harga kue" aria-label="Search"
                        aria-describedby="search-addon" />
                </form>
            </div>
        </div>

        Add-->
        <!-- <div class="row mt-5">
            <div class="col">
                <nuxt-link to="/product/add">
                    <div class="btn add center">Tambah Kue</div>
                </nuxt-link>                
            </div>
        </div> -->

        <!--Catalogue-->
        <!-- <div class="catalogue p-4">
            <div class="row cake gy-5">
                <div v-for="(cake, i) in cakeFiltered" :key="i" class="col-lg-3 col-md-4 col-sm-2 d-flex mt-4">
                    <div class="card flex-fill rounded-4 shadow p-3">
                        <img :src="cake.foto_kue" alt="img-cake" class="card-img-top">
                        <div class="card-body">
                            <h5 class="mt-3">{{ cake.nama_kue }}</h5>
                            <h3 class="fw-bold">{{ cake.harga }}</h3>
                            <div class="text-end my-2">
                                <nuxt-link :to="`/catalogue/${cake.id}`">
                                    <button class="btn mt-3 rounded-5">Beli</button>
                                </nuxt-link>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div> -->

        <!--Modal-->
        <div class="modal fade center" id="exampleModal" tabindex="-1" aria-labelledby="exampleModalLabel"
            aria-hidden="true">
            <div class="modal-dialog modal-dialog-centered modal-md p-4">
                <div class="modal-content">
                    <div class="modal-header">
                        <div class="modal-title fs-5" id="exampleModalLabel"></div>
                        <button type="button" class="btn-close" data-bs-dismiss="modal" aria-label="Close"></button>
                    </div>
                    <div class="modal-body text-center">
                        <h5>Apakah anda yakin akan menghapus produk ini? {{ selectCake.nama_kue }}</h5>
                    </div>
                    <div class="modal-footer">
                        <button type="button" class="btn edit rounded-5" data-bs-dismiss="modal">Batal</button>
                        <button type="button" class="btn delete rounded-5" data-bs-dismiss="modal"
                            @click="deleteCake(selectCake.id)">Hapus</button>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Junge&display=swap');
@import url('https://fonts.googleapis.com/css2?family=Kavoon&family=Miltonian+Tattoo&family=Poppins:ital,wght@0,100;0,200;0,300;0,400;0,500;0,600;0,700;0,800;0,900;1,100;1,200;1,300;1,400;1,500;1,600;1,700;1,800;1,900&family=Red+Rose:wght@300..700&display=swap');


h2 {
    font-family: "Junge", cursive;
}

h3,
h5,
h6,
.form-control,
.btn,
td {
    font-family: "Poppins", sans-serif;
}

.form-control {
    font-size: 14px;
    height: 45px;
    border: 1px solid #C6AC7B;
}

.custom {
    background-color: #C6AC7B;
    color: white;
    height: 20px;
}

.btn {
    width: 175px;
    margin-right: 10px;
    font-size: 17px;
    color: white;
    background-color: #C6AC7B;
}

.cake {
    padding: 50px;
}

.categories img {
    width: 100px;
}

.card {
    border: 1px solid #C6AC7B;
}

.add {
    width: 200px;
    font-size: 20px;
    margin-left: 200px;
}

table {
    width: 100%;
}

td {
    font-size: 18px;
}

table img {
    width: 100px;
    margin-left: 20px;
}

hr {
    margin-top: 25px;
    border: 1px solid #C6AC7B;

}

table i {
    font-weight: 700;
}

table .edit {
    margin-left: 50px;
}

table .delete {
    margin-left: 5px;
}

img {
    width: 100px;

}

.delete {
    margin-left: 25px;
}

.modal {
    height: 300px;
}

.modal-header,
.modal-content,
.modal-footer {
    border: none;
}

.modal-dialog {
    background-color: white;
}

.modal-footer .btn {
    width: 100px;
}

.modal-footer .delete {
    background-color: red !important;
}
</style>