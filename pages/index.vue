<template>
  <div class="container-fluid pt-2 pb-5">
    <div class="wlc text-center text-dark">
      <h3>Selamat Datang</h3> <i class="bi bi-magic fs-3"></i>
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
          <img src="../assets/img/bg-carousel-1.webp" class="d-block w-100 img" alt="...">
          <div class="carousel-caption d-none d-md-block">
            <h5>Buku Adalah Gudangnya Ilmu</h5>
          </div>
        </div>
        <div class="carousel-item">
          <img src="../assets/img/bg-carousel-2.webp" class="d-block w-100" alt="...">
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
        <nuxt-link to="/pengunjung/tambah" style="text-decoration: none;">
          <div class="card bg-pengunjung rounded-5 text-dark text-center mb-4">
            <div class="card-body">
              <h2>Pengunjung</h2>
            </div>
          </div>
        </nuxt-link>
      </div>


      <div class="col-lg-6">
        <nuxt-link to="/buku/caribuku" style="text-decoration: none;">
          <div class="card bg-buku rounded-5 text-dark text-center mb-4">
            <div class="card-body">
              <h2>Cari Buku</h2>
            </div>
          </div>
        </nuxt-link>
      </div>
    </div>

    <h1 class="mt-5 fw-semibold mx-5">Statistik</h1>

    <div class="row mt-2 p-5 statistik justify-content-center">
      <div class="col-lg-5">
        <div class="card rounded-4 text-dark text-center mb-4 bg-secondary bg-opacity-25">
          <div class="card-body">
            <h2>{{ jmlPengunjung }} Pengunjung</h2>
          </div>
        </div>
      </div>

      <div class="col-lg-5">
        <div class="card rounded-4 text-dark text-center mb-4 bg-info bg-opacity-25">
          <div class="card-body">
            <h2>{{ jmlBuku }} Buku</h2>
          </div>
        </div>
      </div>
    </div>

  </div>
</template>

<script setup>
const supabase = useSupabaseClient()
const jmlBuku = ref()
const jmlPengunjung = ref()

const getjmlPengunjung = async () => {
  const { data, count } = await supabase
    .from('pengunjung')
    .select('*', { count: 'exact' })
  if (data) jmlPengunjung.value = count
}

const getjmlBuku = async () => {
  const { data, count } = await supabase
    .from('buku')
    .select('*', { count: 'exact' })
  if (data) jmlBuku.value = count
}

onMounted(() => {
  getjmlPengunjung()
  getjmlBuku()
}
)
</script>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Judson:ital,wght@0,400;0,700;1,400&display=swap');

h3,
h2,
h1 {
  font-family: "Poppins", sans-serif;
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
  background-image: url('../assets/img/bg-home-kunjungan.webp');
  background-repeat: no-repeat;
  background-position: center center;
  background-size: cover;
}

.card.bg-buku {
  background: url('../assets/img/bg-home-cari-buku.webp') no-repeat center center;
  background-size: cover;
}

.icon {
  width: 20px;
}


@media only screen and (max-width: 600px) {

  .card,
  .carousel-item {
    height: 9em;
  }

  .card-body h2 {
    font-size: large;
    margin-top: 0;
    text-decoration: black;
  }

  .img {
    height: 100%;
    background-size: cover;
  }

  .carousel-item h5 {
    margin-top: 2px;
  }

  .statistik .card {
    height: 7rem;
  }

  .statistik .card h2 {
    padding-top: 1.5rem;
  }
}

@media only screen and (min-width: 600px) and (max-width: 890px) {
  .carousel-item {
    height: 15em;
  }
}

</style>