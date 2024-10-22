<script setup>
const supabase = useSupabaseClient()
const customers = ref([])
const cakes = ref([])


const getCustomer = async () => {
    const { data, error } = await supabase.from('customer').select(`*, produk(*)`)
    if (data) {
    customers.value = data
    }
}

const getCake = async () => {
    const { data, error } = await supabase.from('produk').select(`*, kategori(*)`)
    if (data) {
    cakes.value = data
    }
}


onMounted (() => {
    getCustomer()
    getCake()
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
                <h2 class="mt-3">Daftar Pesanan</h2>
            </div>
        </div>

        <div class="row mt-5 justify-content-center">
            <div v-for="(customer, i) in customers" :key="i" class="col-lg-5">
                <div class="card add rounded-4 shadow">
                    <div class="card-body">
                        <div class="row p-3">
                            <div class="col-md-7">
                                <ul>
                                    <li class="list-group-item name fw-semibold">{{ customer.nama_pembeli }}</li>
                                    <li class="list-group-item">{{ customer.alamat_lengkap }}</li>
                                    <li class="list-group-item">{{ customer.no_hp }}</li>
                                    <li class="list-group-item cake fw-semibold">{{ customer.produk.nama_kue }}</li>
                                </ul>
                            </div>
                            <div class="col-md-4">
                                <img :src="customer.produk?.foto_kue" alt="img-cake" class="rounded-3">
                            </div>
                        </div>
                        <div class="row text-center mt-3">
                            <div class="col">
                                <button class="btn complited rounded-5 m-2" data-bs-toggle="modal" data-bs-target="#complitedModal">Tandai selesai</button>
                            </div>
                            <div class="col">
                                <button class="btn btn-danger rounded-5 m-2" data-bs-toggle="modal" data-bs-target="#deleteModal">Batalkan pesanan</button>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>

        <!--Delete Modal-->
        <div class="modal fade center" id="deleteModal" tabindex="-1" aria-labelledby="deleteModalLabel" aria-hidden="true">
            <div class="modal-dialog modal-dialog-centered modal-md p-4">
                <div class="modal-content">
                <div class="modal-header">
                    <div class="modal-title fs-5" id="exampleModalLabel"></div>
                    <button type="button" class="btn-close" data-bs-dismiss="modal" aria-label="Close"></button>
                </div>
                <div class="modal-body text-center">
                    <h5>Apakah anda yakin akan menghapus pesanan ini?</h5>
                </div>
                <div class="modal-footer">
                    <button type="button" class="btn rounded-5" data-bs-dismiss="modal">Batal</button>
                    <button type="button" class="btn delete rounded-5">Hapus</button>
                </div>
                </div>
            </div>
        </div>

        <!--Complited Modal-->
        <div class="modal fade center" id="complitedModal" tabindex="-1" aria-labelledby="complitedModalLabel" aria-hidden="true">
            <div class="modal-dialog modal-dialog-centered modal-md p-4">
                <div class="modal-content">
                <div class="modal-header">
                    <div class="modal-title fs-5" id="exampleModalLabel"></div>
                    <button type="button" class="btn-close" data-bs-dismiss="modal" aria-label="Close"></button>
                </div>
                <div class="modal-body text-center">
                    <h5>Apakah anda yakin pesanan ini selesai?</h5>
                </div>
                <div class="modal-footer">
                    <button type="button" class="btn rounded-5" data-bs-dismiss="modal">Batal</button>
                    <button type="button" class="btn btn-light rounded-5">Ya</button>
                </div>
                </div>
            </div>
        </div>

    </div>
</template>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Kavoon&family=Miltonian+Tattoo&family=Poppins:ital,wght@0,100;0,200;0,300;0,400;0,500;0,600;0,700;0,800;0,900;1,100;1,200;1,300;1,400;1,500;1,600;1,700;1,800;1,900&family=Red+Rose:wght@300..700&display=swap');


h2, li, .btn {
    font-family: "Poppins", sans-serif;
}

.list-group-item {
    font-size: 20px;
    margin-top: 8px;
}

.name {
    font-size: 25px
}

.cake {
    margin-top: 20px;
    font-size: 20px;
}

img {
    width: 175px;
}

.btn-danger {
    background-color: red !important;
}

.btn {
    width: 200px;
    font-size: 17px;
    color: white;
    background-color: #C6AC7B;
}

.delete {
    margin-left: 25px
}

.modal {
    height: 300px;
}

.modal-header, .modal-content, .modal-footer {
    border: none;
}

.modal-dialog {
    background-color: white;
}

.modal-footer .btn {
    width: 100px;
}

.modal-footer .btn-light {
    background-color: white !important;
    border: 3px solid #C6AC7B;
    color: black;
}

.modal-footer .delete {
    background-color: red !important;
}

</style>
