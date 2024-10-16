<template>
    <div class="container-fluid">
        <div class="row my-5">
            <div class="col-lg-6">
                <nuxt-link to="/siswa/">
                    <div class="card bg-siswa rounded-5">
                        <div class="card-body">
                            <h2>siswa</h2>
                        </div>
                    </div>
                </nuxt-link>
            </div>

            <div class="col-lg-6">
                <nuxt-link to="/guru/tambah">
                    <div class="card bg-guru rounded-5">
                        <div class="card-body">
                            <h2>guru</h2>
                        </div>
                    </div>
                </nuxt-link>
              
            </div>
        </div>
        <div class="d-flex justify-content-between">
           

            <nuxt-link to="/" class="btn btn-danger btn-lg rounded-5 px-5">
              Logout
            </nuxt-link>
          </div>
    </div>
</template>
<style scoped>
.card {
    height: 250px;
    box-shadow: 1px 1px 10px #424242;
}

.bg-siswa {
    background-image: url('~/assets/img/absensi.jpg');
    background-repeat: no-repeat;
    background-position: center center;
    background-size: cover;
}
    .bg-guru {
    background: url('~/assets/img/siswa.jpg') no-repeat center center;
    background-size: cover;
}
</style>