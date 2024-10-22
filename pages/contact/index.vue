<template>
    <div class="container-fluid pt-4">
        
        <div class="row">
            <div class="col-lg-1 text-end mt-2">
                <nuxt-link to="/" style="text-decoration: none; color: black;">
                    <i class="bi bi-arrow-left-circle fs-2"></i>
                </nuxt-link>
            </div>
            <div class="col-lg-10">
                <h2 class="mt-3">Contact us</h2>
            </div>
        </div>

        <!--contact-->
        <div class="row contact p-5">
            <div class="col p-5">
                <div class="card rounded-3">
                    <div class="row">
                        <div class="col-md-6 p-5">
                            <div class="p-3">
                                <h2>Hubungi Kami</h2>
                            <h6 class="mt-3">Melayani pertanyaan dan permasalahan customer 24jam</h6>
                            </div>
                            <form action="" class="p-3">
                                <div class="row">
                                    <div class="col-md-6">
                                        <div class="mb-3">
                                            <label for="exampleInput" class="form-label">Nama</label>
                                            <input type="text" class="form-control">
                                        </div>
                                    </div>
                                    <div class="col-md-6">
                                        <div class="mb-3">
                                            <label for="exampleInput" class="form-label">No. Hp</label>
                                            <input type="text" class="form-control">
                                        </div>
                                    </div>
                                </div>
                                <div class="mb-3">
                                    <label for="exampleInput" class="form-label">E - mail</label>
                                    <input type="email" class="form-control">
                                </div>
                                <div class="mb-3">
                                    <label for="exampleInput" class="form-label">Pesan atau pertanyaan</label>
                                    <textarea class="form-control"></textarea>
                                </div>
                                <div class="text-center">
                                    <div class="btn mt-4 rounded-5">Kirim</div>
                                </div>
                            </form>
                        </div>
                        <div class="col-md-6">
                            <div class="card">
                                <div class="card-body">
                                    <!-- <img src="~/assets/img/bgcake-contact.jpg" alt="img-contact" class="rounded-3"> -->
                                </div>
                            </div>
                        </div>
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

h5, h6, label, .btn, .contact h2 {
    font-family: "Poppins", sans-serif;
}

/* img {
    width: 545px;
    height: 615px;
} */

.card-body {
  background: url('~/assets/img/bgcake-contact.jpg') no-repeat center center;
  background-size: cover;
  height: 650px;
}

/* .img {
    margin-left: 5px;
} */

.btn {
    width: 100px;
    /* margin-right: 10px; */
    font-size: 17px;
    color: white;
    background-color: #C6AC7B;
}

textarea {
    height: 100px;
}

input, textarea, .card {
    border: 1px solid #C6AC7B;
}

@media only screen and (max-width: 600px) {
    
}
</style>