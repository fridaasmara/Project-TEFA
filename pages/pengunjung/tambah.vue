<template>
  <div class="container-fluid pt-2 pb-5">
    <div class="col-md-6 offset-md-3">
      <h2 class="text-center text-dark">Isi Catatan Kunjungan</h2>
      <div class="row">
        <div class="col text-end">
          <nuxt-link to="/">
            <button class="btn btn-primary mb-5">Kembali</button>
          </nuxt-link>
        </div>
      </div>
      <form>
        <div class="py-3">
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
        <div class="text-center">
          <nuxt-link to="../pengunjung/riwayat">
            <button type="submit" class="btn btn-primary my-2 text-center ">Kirim</button>
          </nuxt-link>
        </div>
      </form>
    </div>
  </div>
</template>

<style scoped>
.container-fluid {
  padding-bottom: 10em;
  background-color: #E5F1FD;
}

h2 {
  margin-top: 225px;
  margin-bottom: 2em;
}

form {
  border-radius: 2.5em;
  background-color: white;
  padding: 2em;

}

input {
  background-color: #E7F5F5;
  box-shadow: 1px 1px 10px #424242;
}

select {
  background-color: #E7F5F5;
  box-shadow: 1px 1px 10px #424242;
}

.btn {
  background-color: #394367;
}

label {
  font-size: 15px;
}

@media only screen and (max-width: 600px) {
  h2 {
    font-size: large;
  }
  .btn {
    font-size: 1.5vh;
    margin-right: 2em;
  } 
}
</style>
