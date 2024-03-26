<template>
  <div class="container-fluid pb-5">
    <div class="text-center text-dark">
      <h3>Riwayat Kunjungan</h3>
    </div>
    <div class="input-group flex-nowrap rounded my-5">
      <input type="search" class="form-control" placeholder="Cari..." aria-label="Search" />
      <span class="input-group-text"><i class="bi bi-search"></i></span> 
    </div>
    <div class="row my-5 mx-2 p-1">
      <div class="col">
        <div class="text-muted">Saat ini : 1 dari 1 kunjungan</div>
      </div>
      <div class="col text-end">
        <nuxt-link to="../pengunjung/tambah">
          <button class="btn btn-primary first">Kembali</button>
        </nuxt-link>
        <nuxt-link to="../buku/caribuku">
          <button class="btn btn-primary">Cari buku</button>
        </nuxt-link>
      </div>
    </div>

    <div class="table table-responsive">
      <table class="border-dark w-100">
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

  </div>
</template>

<style scoped>
.input-group-text {
  background-color: #fff;
  border-left: none !important;
  margin-right: 25px;
}
.form-control {
  border-right: none;
  margin-left: 25px;
}
.container-fluid {
  background-color: #E5F1FD;
}

.btn {
  margin-right: 20px;
  background-color: #394367;
}

h3 {
  padding-top: 225px;
}

th {
  padding-left: 20px;
  padding-right: 20px;
}

td {
  padding-left: 20px;
  padding-right: 20px;
}

@media only screen and (max-width: 600px) {
  h3 {
    font-size: large;
  }
  .btn {
    font-size: 1.3vh;
    margin-right: 0.7em;
  }
  .first {
    margin-bottom: 5px;
    margin-left: 20px;
  }
  .input-group-text {
    margin-right: 1.5em;
  }
}


/* @media (min-width: 360px) and (max-width: 430px)   */
   /* .btn {
    font-size: 1.3vh;
    margin-right: 0.7em;
  }
  .first {
    margin-bottom: 5px;
    margin-left: 20px;
  }
  .input-group-text {
    margin-right: 1.5em;
  }
} */
</style>