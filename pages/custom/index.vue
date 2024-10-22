<template>
    <div class="container-fluid pt-4">

        <div class="row">
            <div class="col-lg-1 text-end mt-2">
                <nuxt-link to="/product" style="text-decoration: none; color: black;">
                    <i class="bi bi-arrow-left-circle fs-2"></i>
                </nuxt-link>
            </div>
            <div class="col-lg-10 text-center">
                <h3 class="mt-3">Costum Your Cake</h3>
            </div>
        </div>

        <!-- <div class="row costum mt-5 p-5 justify-content-center">
                <div class="col-lg-4">
                    <div class="card card-costum rounded-4">
                        <div class="card-body text-center">
                            <img src="~/assets/img/bgcake-custom.png" alt="img-cake">
                        </div>
                    </div>
                </div>
                <div class="col-lg-5 content">
                    <h5 class="fw-bold">Costum kue keinginanmu, </h5>
                    <h5>agar moment perayaan terasa lebih bermakna</h5>
                    <nuxt-link href="https://wa.me/6281224703915" style="text-decoration: none; color: black;">
                        <button class="btn pesan rounded-5">Pesan via Whatsapp</button>
                    </nuxt-link>
                </div>
        </div> -->


        <div class="row costum mt-5 p-5 justify-content-center">
            <div class="col-lg-3">
                <div class="card card-custom rounded-4">
                    <div class="card-body text-center">
                        <img src="~/assets/img/bgcake-custom.png" alt="img-custom" class="img-custom mt-1">
                    </div>
                </div>
            </div>
            <div class="col-lg-6 content">
                <h5 class="fw-bold">Custom kue keinginanmu, </h5>
                <h5>agar moment perayaan terasa lebih bermakna</h5>
                <nuxt-link href="https://wa.me/6281224703915" style="text-decoration: none; color: black;">
                    <button class="btn pesan rounded-5">Pesan via Whatsapp</button>
                </nuxt-link>
            </div>
        </div>

    </div>
</template>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Kavoon&family=Miltonian+Tattoo&family=Poppins:ital,wght@0,100;0,200;0,300;0,400;0,500;0,600;0,700;0,800;0,900;1,100;1,200;1,300;1,400;1,500;1,600;1,700;1,800;1,900&family=Red+Rose:wght@300..700&display=swap');


h3,
h5,
.btn {
    font-family: "Poppins", sans-serif;
}

.text {
    margin-left: 75px;
}

/* .card {
    height: 300px;
} */

.card-custom {
    max-width: fit-content;
    border: 1px solid #C6AC7B;
}

img {
    /* width: 300px; */
    height: 270px;
}

.pesan {
    width: 225px;
    margin-top: 50px;
    margin-left: 20px;
    background-color: white;
    color: black;
    border: 3px solid #C6AC7B;
}

.container-fluid {
    background-color: #F0EDDC;
}

.content {
    margin-left: 50px;
}

/* img {
    width: 230px;
} */
</style>