<template>
    <div class="container-fluid pt-4">

        <div class="row">
            <div class="col-lg-1 text-end mt-2">
                <i class="bi bi-arrow-left-circle fs-2"></i>
            </div>
            <div class="col-lg-10">
                <h2 class="mt-3">Detail</h2>
            </div>
        </div>


        <!--Detail-->
        <div class="row mt-5 justify-content-center">
            <div class="col-lg-3">
                <div class="card img-cake rounded-4 shadow">
                    <div class="card-body text-center">
                        <img src="~/assets/img/bgcake-detail.png" alt="img-cake" class="mt-1 rounded-3">
                    </div>
                </div>
            </div>
            <div class="col-lg-5">
                <div class="card mb-5 rounded-4">
                    <div class="card-body">
                        <ul>
                            <li class="list-group-item name fw-semibold">Butterfly cake</li>
                            <li class="list-group-item">Birthday cake</li>
                            <li class="list-group-item">Ukuran 12cm</li>
                            <li class="list-group-item price fw-bold">Rp. 35.000</li>
                        </ul>
                        <div class="text-end mt-5 mb-5">
                            <nuxt-link to="../product/edit">
                                <button class="btn edit rounded-5">Edit</button>
                            </nuxt-link>
                            <button class="btn btn-danger rounded-5" data-bs-toggle="modal" data-bs-target="#exampleModal">Hapus</button>
                        </div>
                    </div>
                </div>
            </div>
        </div>

        <!--Modal-->
        <div class="modal fade center" id="exampleModal" tabindex="-1" aria-labelledby="exampleModalLabel" aria-hidden="true">
            <div class="modal-dialog modal-dialog-centered modal-md p-4">
                <div class="modal-content">
                <div class="modal-header">
                    <div class="modal-title fs-5" id="exampleModalLabel"></div>
                    <button type="button" class="btn-close" data-bs-dismiss="modal" aria-label="Close"></button>
                </div>
                <div class="modal-body text-center">
                    <h5>Apakah anda yakin akan menghapus produk ini?</h5>
                </div>
                <div class="modal-footer">
                    <button type="button" class="btn edit rounded-5" data-bs-dismiss="modal">Batal</button>
                    <button type="button" class="btn btn-danger rounded-5">Hapus</button>
                </div>
                </div>
            </div>
        </div>

    </div>
</template>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Kavoon&family=Miltonian+Tattoo&family=Poppins:ital,wght@0,100;0,200;0,300;0,400;0,500;0,600;0,700;0,800;0,900;1,100;1,200;1,300;1,400;1,500;1,600;1,700;1,800;1,900&family=Red+Rose:wght@300..700&display=swap');


h2, h5, h6, li, .btn, .modal {
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

.img-cake {
    height: 360px;
}

h6 {
    margin-top: 125px;
}

.edit {
    width: 100px;
    border: 3px solid #C6AC7B;
}

.btn-danger {
    width: 100px;
    margin-left: 30px;
}

.button {
    margin-left: 20px;   
}

.text-end {
    margin-right: 30px;
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

img {
    width: 250px;
}

</style>