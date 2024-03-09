<template>
  <div class="container-fluid">
    <div class="text-center text-dark">
      <h3>Cari Buku</h3>
    </div>
    <div class="row align-item-center">
      <div class="col">
        <div class="input-group rounded my-5">
          <input type="search" class="form-control rounded" placeholder="Cari buku" aria-label="Search"
            aria-describedby="search-addon" /><img src="~/assets/img/search.png" class="img-search" alt="">
        </div>
      </div>
      <div class="col-auto">
        <select class="form-control form-select mb-2" id="exampleFormControlSelect1">
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
    <div class="row my-5">
      <div class="col">
        <div class="rekomen text-dark">Rekomendasi</div>
      </div>
      <div class="col text-end">
        <nuxt-link to="/">
          <button class="btn btn-primary">Kembali</button>
        </nuxt-link>

        <nuxt-link to="../pengunjung/tambah">
          <button class="btn btn-primary">Kunjungan</button>
        </nuxt-link>
      </div>
    </div>

    <div class="row book">
      <div class="col-lg-2">
        <div class="card">
          <img src="~/assets/img/Aboycalledocean.jpg" class="card-img-top" alt="...">
          <div class="card-body">
            <h5 class="card-title">A Boy Called Ocean</h5>
            <a href="#" class="btn btn-primary my-2 center">Lihat Detail</a>
          </div>
        </div>
      </div>
      <div class="col-lg-2">
        <div class="card">
          <img src="~/assets/img/Masteringbasicenglish.jpg" class="card-img-top" alt="...">
          <div class="card-body">
            <h5 class="card-title">Mastering Basic English</h5>
            <a href="#" class="btn btn-primary my-2 justify-content-center">Lihat Detail</a>
          </div>
        </div>
      </div>
      <div class="col-lg-2">
        <div class="card">
          <img src="~/assets/img/Offtherecord3.jpg" class="card-img-top" alt="...">
          <div class="card-body">
            <h5 class="card-title">Off The Record 3</h5>
            <a href="#" class="btn btn-primary my-2">Lihat Detail</a>
          </div>
        </div>
      </div>
      <div class="col-lg-2">
        <div class="card mb-3">
          <img src="~/assets/img/Loveforimperfectthings.jpg" class="card-img-top" alt="...">
          <div class="card-body">
            <h5 class="card-title">Love for Imperfect Things</h5>
            <a href="#" class="btn btn-primary my-3">Lihat Detail</a>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>


<style scoped>
h3 {
  margin-top: 250px;
}

input {
  margin-right: 20px;
}

.rekomen {
  font-size: 25px;
}

.btn {
  margin-right: 20px;
  background-color: #394367;
}

/* .book {
  position: relative;
} */

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
</style>