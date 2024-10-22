<template>
    <div class="container-fluid pt-4">

        <div class="row">
            <div class="col-lg-1 text-end mt-2">
                <nuxt-link to="/product" style="text-decoration: none; color: black;">
                    <i class="bi bi-arrow-left-circle fs-2"></i>
                </nuxt-link>            
            </div>
            <div class="col-lg-10">
                <h2 class="mt-3">Edit Kue</h2>
            </div>
        </div>

        <div class="row mt-5 justify-content-center">
            <div class="col-lg-3">
                <div class="card add rounded-4 shadow">
                    <div class="card-body text-center p-3">
                        <img src="~/assets/img/bgcake-detail.png" alt="img-cake" class="mt-2 rounded-3">
                    </div>
                </div>
            </div>
            <div class="col-lg-4">
                <div class="card mb-5 rounded-4 shadow">
                    <div class="card-body">
                        <form class="input-group p-3">
                            <div class="mb-3">
                                <label for="exampleFormControlInput1" class="form-label">Nama Kue</label>
                                <input type="text" class="form-control" id="exampleFormControlInput1">
                            </div>
                            <div class="mb-3">
                                <label for="exampleFormControlInput1" class="form-label">Kategori</label>
                                <input type="text" class="form-control" id="exampleFormControlInput1">
                            </div>
                            <div class="mb-3">
                                <label for="exampleFormControlInput1" class="form-label">Ukuran</label>
                                <input type="text" class="form-control" id="exampleFormControlInput1">
                            </div>
                            <div class="mb-3">
                                <label for="exampleFormControlInput1" class="form-label">Harga</label>
                                <input type="text" class="form-control" id="exampleFormControlInput1">
                            </div>
                            <div class="text-end mt-3">
                                <nuxt-link to="/product">
                                    <button type="submit" class="btn rounded-5">Edit</button>
                                </nuxt-link>
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
    margin-left: 120px;
    font-size: 20px;
    color: white;
    background-color: #C6AC7B;

}

.add {
    height: 325px;
}

h6 {
    margin-top: 125px;
}

img {
    width: 250px;
}

</style>