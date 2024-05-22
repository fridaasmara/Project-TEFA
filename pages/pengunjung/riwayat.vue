<template>
  <div class="container-fluid">
    <div class="text-center text-dark">
      <h3>Riwayat Kunjungan</h3>
    </div>
    <div class="input-group rounded my-5">
      <input type="search" class="form-control rounded" placeholder="Cari..." aria-label="Search"
        aria-describedby="search-addon" /><img src="~/assets/img/search.png" class="img-search" alt="">
    </div>
    <div class="row my-5">
      <div class="col">
        <div class="text-muted">Saat ini : 1 dari 1 kunjungan</div>
      </div>
      <div class="col text-end">
        <nuxt-link to="../pengunjung/tambah">
          <button class="btn btn-primary">Kembali</button>
        </nuxt-link>
        <nuxt-link to="../buku/utama"><button class="btn btn-primary">Cari buku</button>
        </nuxt-link>

      </div>
    </div>

    <table class="table">
      <thead>
        <tr>
          <th>No</th>
          <th>Tanggal</th>
          <th>Waktu</th>
          <th>Nama</th>
          <th>Keanggotaan</th>
          <th>Kelas</th>
          <th>Keperluan</th>
        </tr>
      </thead>
      <tbody>
        <tr>
          <td>1</td>
          <td>7 Maret 2024</td>
          <td>11.10.00</td>
          <td>Frida </td>
          <td>Siswa</td>
          <td>XI PPLG 3</td>
          <td>Membaca</td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<style scoped>
.btn {
  margin-right: 20px;
  background-color: #394367;
}

h3 {
  padding-top: 250px;
}

.img-search {
  margin-top: 5px;
  width: 20px;
  height: 20px;
}
</style>