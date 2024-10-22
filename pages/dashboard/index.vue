<template>
    <div class="container-fluid pt-4">
        
        <div class="row">
            <div class="col-lg-1 text-end mt-2">
                <i class="bi bi-arrow-left-circle fs-2"></i>
            </div>
            <div class="col-lg-10">
                <h2 class="mt-3">Dashboard</h2>
            </div>
        </div>

        <div class="row mt-5 justify-content-center">
            <div class="col-lg-4">
                <nuxt-link to="/product" class="text-dark" style="text-decoration: none;">
                    <div class="card rounded-3">
                        <div class="card-body shadow p-3 text-center rounded">
                            <img src="~/assets/img/cakecake.png" alt="img-product" class="mt-3 rounded-3">
                            <h5 class="mt-3">Daftar Produk</h5>
                        </div>
                    </div>
                </nuxt-link>
            </div>
            <div class="col-lg-4">
                <nuxt-link to="/customer" class="text-dark" style="text-decoration: none;">
                    <div class="card rounded-3">
                        <div class="card-body shadow p-3 text-center rounded">
                            <img src="~/assets/img/notes.png" alt="img-product" class="mt-3 rounded-3">
                            <h5 class="mt-3">Daftar Pesanan</h5>
                        </div>
                    </div>
                </nuxt-link>
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

h5, h6 {
    font-family: "Poppins", sans-serif;
}

</style>