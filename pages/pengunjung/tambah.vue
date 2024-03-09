<template>
  <div class="container">
    <div class="form col-md-6 offset-md-3 mt-5">
      <h2 class="text-center text-dark">Isi Catatan Kunjungan</h2>
      <form>
        <div class="mb-3">
          <label for="exampleFormControlInput1">Nama</label>
          <input type="text" class="form-control" id="exampleFormControlInput1" />
        </div>
        <div class="form-group py-3">
          <label for="exampleFormControlSelect1">Keanggotaan</label>
          <select class="form-control form-select" id="exampleFormControlSelect1">
            <option value="Guru">Guru</option>
            <option value="Staf">Staf</option>
            <option value="Siswa">Siswa</option>
            <option value="Umum">Umum</option>
          </select>
        </div>
        <div class="form-group py-3">
          <label for="exampleFormControlSelect1">Kelas Lengkap</label>
          <div class="row">
            <div class="col-md-4">
              <select class="form-control form-select mb-2" id="exampleFormControlSelect1">
                <option disable value=" ">Tingkat</option>
                <option value="X">X</option>
                <option value="XI">XI</option>
                <option value="XII">XII</option>
              </select>
            </div>
            <div class="col-md-4">
              <select class="form-control form-select mb-2" id="exampleFormControlSelect1">
                <option disable value=" ">Jurusan</option>
                <option value="PPLG">PPLG</option>
                <option value="TJKT">TJKT</option>
                <option value="TBSM">TBSM</option>
                <option value="TOI">TOI</option>
                <option value="DKV">DKV</option>
              </select>
            </div>
            <div class="col-md-4">
              <select class="form-control form-select mb-2" id="exampleFormControlSelect1">
                <option disable value=" ">Kelas</option>
                <option value="1">1</option>
                <option value="2">2</option>
                <option value="3">3</option>
                <option value="4">4</option>
              </select>
            </div>
          </div>
        </div>
        <div class="form-group py-3">
          <label for="exampleFormControlSelect1">Keperluan</label>
          <select class="form-control form-select" id="exampleFormControlSelect1">
            <option value="Membaca">Membaca buku</option>
            <option value="Pinjam">Meminjam buku</option>
            <option value="Kembalikan">Mengembalikan</option>
          </select>
        </div>
        <nuxt-link to="../pengunjung/riwayat">
          <button type="submit" class="btn btn-primary my-2 text-center">Kirim</button>
        </nuxt-link>
      </form>
    </div>
  </div>
</template>

<style scoped>
h2 {
  margin-top: 200px;
  margin-bottom: 100px;
}

input {
  background-color: #E7F5F5;
  box-shadow: 1px 1px 10px #424242;
}

select {
  background-color: #E7F5F5;
  box-shadow: 1px 1px 10px #424242;
}
</style>
