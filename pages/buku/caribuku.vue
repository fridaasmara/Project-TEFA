<template>
  <div class="container-fluid pt-2 pb-5">
    <div class="text-center text-dark">
      <h3>Cari Buku</h3>
    </div>
    <div class="row mt-5 mb-3 p-2 d-flex justify-content-center">
      <div class="col-md-8 mb-2">
        <div class="input-group flex-nowrap rounded">
          <input type="search" class="form-control" placeholder="Cari buku" aria-label="Search" aria-describedby="search-addon"/>
          <span class="input-group-text"><i class="bi bi-search"></i></span> 
        </div>
      </div>
      <div class="col-md-3">
        <select class="form-control form-select" id="exampleFormControlSelect1">
          <option disable value=" ">Kategori</option>
          <option value="Bahasa">Bahasa</option>
          <option value="Kesusastraan">Kesusastraan</option>
          <option value="Umum">Umum</option>
          <option value="Sains & Matematika">Sains & Matematika</option>
          <option value="Seni & Rekreasi">Seni & Rekreasi</option>
          <option value="Sosial">Sosial</option>
          <option value="Sejarah & Geografi">Sejarah & Geografi</option>
        </select>
      </div>
    </div>
    <div class="row mt-4 p-1">
      <div class="col">
        <div class="rekomen text-dark">Rekomendasi</div>
      </div>
      <div class="col text-end">
        <nuxt-link to="/">
          <button class="btn btn-primary first">Kembali</button>
        </nuxt-link>

        <nuxt-link to="../pengunjung/tambah">
          <button class="btn btn-primary">Kunjungan</button>
        </nuxt-link>
      </div>
    </div>

    <div class="row gy-5 my-3 cardbook">
      <div class="col-sm-6 col-md-4 col-lg-2">
        <div class="card">
          <img src="~/assets/img/Aboycalledocean.jpg" class="card-img-top" alt="...">
          <div class="card-body">
            <h5 class="card-title">A Boy Called Ocean</h5>
            <a href="#" class="btn btn-primary my-2 center" @click="showModal">Lihat Detail </a> 
            <detailbuku></detailbuku>
          </div>
        </div>
      </div>
      <div class="col-sm-6 col-md-4 col-lg-2">
        <div class="card">
          <img src="~/assets/img/mariposa1.jpeg" class="card-img-top" alt="...">
          <div class="card-body">
            <h5 class="card-title">Mariposa 2 (part 1)</h5>
            <a href="#" class="btn btn-primary my-2">Lihat Detail</a>
          </div>
        </div>
      </div>
      <div class="col-sm-6 col-md-4 col-lg-2">
        <div class="card">
          <img src="~/assets/img/mariposa2.jpeg" class="card-img-top" alt="...">
          <div class="card-body">
            <h5 class="card-title">Mariposa 2 (part 2)</h5>
            <a href="#" class="btn btn-primary my-2">Lihat Detail</a>
          </div>
        </div>
      </div>
      <div class="col-sm-6 col-md-4 col-lg-2">
        <div class="card">
          <img src="~/assets/img/ppkn.jpeg" class="card-img-top" alt="...">
          <div class="card-body">
            <h5 class="card-title">Pendidikan Pancasila SMK/MAK</h5>
            <a href="#" class="btn btn-primary my-2">Lihat Detail</a>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>


<script>
import detailbuku from '../buku/detailbuku.vue'

export default {
  components: {
    detailbuku
  },
  methods: {
    showModal() {
      const myModal = new bootstrap.Modal(document.getElementById('detailbukuModal'));
      myModal.show();
    }
  }
}
</script>


<style scoped>
.input-group-text {
  background-color: #fff;
  border-left: none !important;
}
.form-control {
  border-right: none;
}

.container-fluid {
  background-color: #E5F1FD;
}

h3 {
  margin-top: 225px;
}

.rekomen {
  font-size: 25px;
  margin-left: 25px;
}

.btn {
  margin-right: 20px;
  background-color: #394367;
}

.cardbook {
  margin-left: 25px;
  margin-right: 25px;
}

.card {
  width: 100%;
  padding: 0;
}

.card-img-top {
  width: 100%;
  height: 100%;
  object-fit: cover;
  object-position: 0 30;
}

.img-search {
  margin-top: 5px;
  width: 20px;
  height: 20px;
}

@media only screen and (max-width: 600px) {
  h3 {
    font-size: large;
  }
  .rekomen {
    font-size: large;
  }
  .btn {
    font-size: 1.3vh;
  }
  .first {
    margin-bottom: 5px;
    margin-left: 20px;
  }
}


</style>