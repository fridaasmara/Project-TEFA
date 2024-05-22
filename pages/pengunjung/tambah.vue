<template>
  <div class="container-fluid pt-2 pb-5">
    <div>
      <h2 class="text-center text-dark">Isi Catatan Kunjungan</h2>
      <div class="row">
        <div class="col text-end mb-5">
          <nuxt-link to="/">
            <button class="btn btn-primary first">Kembali</button>
          </nuxt-link>

          <nuxt-link to="../pengunjung/riwayat">
            <button class="btn btn-primary">Riwayat</button>
          </nuxt-link>
        </div>
      </div>
      <div class="row">
        <div class="col-md-6 offset-md-3">
          <div class="card shadow rounded">
            <div class="card-body">
              <form @submit.prevent="kirimData" class="p-4">
                <div class="py-3">
                  <label for="nama">Nama</label>
                  <input v-model="form.nama" type="text" class="form-control" id="nama" />
                </div>
                <div class="form-group py-3">
                  <label for="keanggotaan">Keanggotaan</label>
                  <select @change="cekKeanggotaan" v-model="form.keanggotaan" class="form-control form-select"
                    id="keanggotaan">
                    <option v-for="(member, i) in members" :key="i" :value="member.id">{{ member.nama }}</option>
                  </select>
                </div>
                <div v-if="form.keanggotaan == '2'" class="form-group py-3">
                  <label for="kelaslengkap">Kelas Lengkap</label>
                  <div class="row">
                    <div class="col-md-4">
                      <select v-model="form.tingkat" class="form-control form-select mb-2" id="kelaslengkap">
                        <option disable value=" ">Tingkat</option>
                        <option value="X">X</option>
                        <option value="XI">XI</option>
                        <option value="XII">XII</option>
                      </select>
                    </div>
                    <div class="col-md-4">
                      <select v-model="form.jurusan" class="form-control form-select mb-2" id="kelaslengkap2">
                        <option disable value=" ">Jurusan</option>
                        <option value="PPLG">PPLG</option>
                        <option value="TJKT">TJKT</option>
                        <option value="TBSM">TBSM</option>
                        <option value="TOI">TOI</option>
                        <option value="DKV">DKV</option>
                      </select>
                    </div>
                    <div class="col-md-4">
                      <select v-model="form.kelas" class="form-control form-select mb-2" id="kelaslengkap3">
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
                  <label for="keperluan">Keperluan</label>
                  <select v-model="form.keperluan" class="form-control form-select" id="keperluan">
                    <option v-for="(item, i) in objectives" :key="i" :value="item.id">{{ item.nama }}</option>
                  </select>
                </div>
                <div class="text-center">
                  <button type="submit" class="btn btn-primary my-2 text-center">Kirim</button>
                </div>
              </form>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>


<script setup>
useHead({ title: "Perpus Digital - Kunjungan" })

const supabase = useSupabaseClient()
const members = ref([])
const objectives = ref([])
const form = ref({
  nama: "",
  keanggotaan: "",
  tingkat: "",
  jurusan: "",
  kelas: "",
  keperluan: "",
})

const kirimData = async () => {
  const { error } = await supabase.from('pengunjung').insert([form.value])
  if (!error) navigateTo('/pengunjung/riwayat')
  console.log(error)
}

const getKeanggotaan = async () => {
  const { data, error } = await supabase.from('keanggotaan').select('*')
  if (data) members.value = data
}

const getKeperluan = async () => {
  const { data, error } = await supabase.from('keperluan').select('*')
  if (data) objectives.value = data
}

const cekKeanggotaan = e => {
  if (e.target.value != '2') {
    form.value.tingkat = ""
    form.value.jurusan = ""
    form.value.kelas = ""
  }
}

onMounted(() => {
  getKeanggotaan()
  getKeperluan()
})

</script>


<style scoped>
h2,
form,
.btn {
  font-family: "Poppins", sans-serif;
}

.container-fluid {
  padding-bottom: 10em;
}

h2 {
  margin-top: 225px;
  margin-bottom: 2em;
}

input {
  background-color: #E7F5F5;
  box-shadow: 1px 1px 10px #424242;
}

select {
  background-color: #E7F5F5;
  box-shadow: 1px 1px 10px #424242;
}

.text-end {
  margin-right: 10rem;
}

.btn {
  margin-right: 2rem;
  background-color: #394367;
}

label {
  font-size: 15px;
}

@media only screen and (max-width: 600px) {
  h2 {
    font-size: large;
  }

  .text-end {
    margin-right: 1rem;
  }

  .btn {
    margin-right: 1rem;
    font-size: 1.5vh;
  }
}
</style>
