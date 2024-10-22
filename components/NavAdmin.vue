<template>
    <nav class="navbar navbar-expand-lg bg-light">
        <div class="container-fluid">
            <i class="bi bi-person-rolodex fs-1"></i>
            <h2 class="navbar-brand fw-semibold" href="#">Admin</h2>
            <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarNav" aria-controls="navbarNav" aria-expanded="false" aria-label="Toggle navigation">
                <span class="navbar-toggler-icon"></span>
            </button>
                <div class="text-end">
                    <h5 class="text-danger" data-bs-toggle="modal" data-bs-target="#logoutModal">Logout</h5>
                </div>
        </div>
    </nav>

    <!--Modal-->
    <div class="modal fade" id="logoutModal" tabindex="-1" aria-labelledby="logoutModalLabel" aria-hidden="true">
        <div class="modal-dialog modal-dialog-centered modal-md p-4">
            <div class="modal-content">
            <div class="modal-header">
                <div class="modal-title fs-5" id="exampleModalLabel"></div>
                <button type="button" class="btn-close" data-bs-dismiss="modal" aria-label="Close"></button>
            </div>
            <div class="modal-body text-center">
                <h5>Apakah anda yakin akan keluar dari website ini?</h5>
            </div>
            <div class="modal-footer">
                <button type="button" class="btn edit rounded-5" data-bs-dismiss="modal">Batal</button>
                <nuxt-link to="/logout">
                    <button type="button" class="btn btn-danger rounded-5">Ya</button>
                </nuxt-link>
            </div>
            </div>
        </div>
    </div>

</template>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Kavoon&family=Miltonian+Tattoo&family=Poppins:ital,wght@0,100;0,200;0,300;0,400;0,500;0,600;0,700;0,800;0,900;1,100;1,200;1,300;1,400;1,500;1,600;1,700;1,800;1,900&family=Red+Rose:wght@300..700&display=swap');

i {
    margin-left: 2rem;
}

h2 {
    margin-top: 1rem;
    font-size: 2rem;

}

/* .navbar-collapse {
    margin-right: 5rem;
} */

.text-end {
    margin-right: 2rem;
}

h2, h5, .btn, .modal {
    font-family: "Poppins", sans-serif;

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


</style>