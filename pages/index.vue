<template>
  <div class="container-fluid pt-2 pb-5">
    <div class="wlc text-center text-dark">
      <h3>Selamat Datang</h3>
      <img src="../assets/icon/wand-magic-sparkles-solid (1).svg" alt="" class="icon">
    </div>

    <div id="carouselExampleCaptions" class="carousel slide mt-5 p-2" data-bs-ride="carousel">
      <div class="carousel-indicators">
        <button type="button" data-bs-target="#carouselExampleCaptions" data-bs-slide-to="0" class="active"
          aria-current="true" aria-label="Slide 1"></button>
        <button type="button" data-bs-target="#carouselExampleCaptions" data-bs-slide-to="1"
          aria-label="Slide 2"></button>
      </div>
      <div class="carousel-inner">
        <div class="carousel-item active">
          <img src="../assets/img/bg-carousel-1.jpg" class="d-block w-100 img" alt="...">
          <div class="carousel-caption d-none d-md-block">
            <h5>Buku Adalah Gudangnya Ilmu</h5>
          </div>
        </div>
        <div class="carousel-item">
          <img src="../assets/img/bg-carousel-2.jpg" class="d-block w-100" alt="...">
          <div class="carousel-caption d-none d-md-block">
            <h5>Buku Adalah Gudangnya Ilmu</h5>
          </div>
        </div>
      </div>
      <button class="carousel-control-prev" type="button" data-bs-target="#carouselExampleCaptions"
        data-bs-slide="prev">
        <span class="carousel-control-prev-icon" aria-hidden="true"></span>
        <span class="visually-hidden">Previous</span>
      </button>
      <button class="carousel-control-next" type="button" data-bs-target="#carouselExampleCaptions"
        data-bs-slide="next">
        <span class="carousel-control-next-icon" aria-hidden="true"></span>
        <span class="visually-hidden">Next</span>
      </button>
    </div>

    <div class="row mt-5 p-2">
      <div class="col-lg-6">
        <nuxt-link to="/pengunjung/tambah">
          <div class="card bg-pengunjung rounded-5 text-dark text-center mb-4">
            <div class="card-body">
              <h2>Pengunjung</h2>
            </div>
          </div>
        </nuxt-link>
      </div>


      <div class="col-lg-6">
        <nuxt-link to="/buku/caribuku">
          <div class="card bg-buku rounded-5 text-dark text-center mb-4">
            <div class="card-body">
              <h2>Cari Buku</h2>
            </div>
          </div>
        </nuxt-link>
      </div>
    </div>
  </div>
</template>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Judson:ital,wght@0,400;0,700;1,400&display=swap');

.container-fluid {
  background-color: #E5F1FD;
}

.wlc {
  margin-top: 220px;
}

.carousel-item {
  font-family: "Judson", serif;
  font-weight: 400;
  font-style: italic;
  height: 20em;
}

.carousel-item h5 {
  margin-top: 20px;
}

.card-body h2 {
  margin-top: 25px;
  padding-top: 50px;
}

.card {
  height: 250px;
  box-shadow: 1px 1px 10px #424242;
}

.card.bg-pengunjung {
  background-image: url('../assets/img/bg-home-kunjungan.png');
  background-repeat: no-repeat;
  background-position: center center;
  background-size: cover;
}

.card.bg-buku {
  background: url('../assets/img/bg-home-cari-buku.png') no-repeat center center;
  background-size: cover;
}

.icon {
  width: 20px;
}

@media only screen and (max-width: 600px) {
  .card, .carousel-item {
    height: 9em;
  }
  .card-body h2{
    font-size: large;
    margin-top: 0;
    text-decoration: none;
  }
  .img {
    height: 100%;
    background-size: cover;
  }
  .carousel-item h5 {
    margin-top: 2px;
  } 
}

@media only screen and (min-width: 600px) and (max-width: 890px) {
  .carousel-item {
    height: 15em;
  }
}


</style>