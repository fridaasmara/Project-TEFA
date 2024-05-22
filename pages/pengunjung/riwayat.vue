<template>
  <div class="container-fluid pb-5">
    <div class="text-center text-dark">
      <h3>Riwayat Kunjungan</h3>
    </div>
    <div class="row justify-content-center">
      <div class="col-10">
        <form @submit.prevent="getPengunjung" class="input-group flex-nowrap rounded my-5">
          <input v-model="keyword" type="search" class="form-control" placeholder="Cari..." aria-label="Search" />
          <span class="input-group-text"><i class="bi bi-search"></i></span>
        </form>
      </div>
    </div>
    <div class="row my-3 mx-5">
      <div class="col">
        <p class="text-muted">Menampilkan : {{ visitors.length }} dari {{ jmlPengunjung }} pengunjung</p>
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

    <div class="row p-3">
      <div class="col">
        <div class="card shadow rounded p-4">
          <div class="card-body">
            <div class="table-responsive">
              <table class="table table-striped">
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
                  <tr v-for="(visitor, i) in visitors" :key="i">
                    <td>{{ i + 1 }}</td>
                    <td>{{ visitor.tanggal }}</td>
                    <td>{{ visitor.waktu }}</td>
                    <td>{{ visitor.nama }}</td>
                    <td>{{ visitor.keanggotaan.nama }}</td>
                    <td>{{ visitor.tingkat }} {{ visitor.jurusan }} {{ visitor.kelas }}</td>
                    <td>{{ visitor.keperluan.nama }}</td>
                  </tr>
                </tbody>
              </table>
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
const visitors = ref([])
const jmlPengunjung = ref(0)
const keyword = ref('')

const getPengunjung = async () => {
  const { data, error } = await supabase
    .from('pengunjung')
    .select(`*, keanggotaan(*), keperluan(*)`)
    .order('id', { ascending: false })
    .ilike("nama", `%${keyword.value}%`)
  if (data) visitors.value = data
}

const getjmlPengunjung = async () => {
  const { data, count } = await supabase
    .from('pengunjung')
    .select('*', { count: 'exact' })
  if (data) jmlPengunjung.value = count
}

onMounted(() => {
  getPengunjung()
  getjmlPengunjung()
})
</script>


<style scoped>
h3,
input,
table,
.text-muted,
.btn {
  font-family: "Poppins", sans-serif;
}

.input-group-text {
  background-color: #fff;
  border-left: none !important;
  margin-right: 25px;
}

.form-control {
  border-right: none;
  margin-left: 25px;
}

.btn {
  margin-right: 2rem;
  background-color: #394367;
}

h3 {
  padding-top: 225px;
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

  p {
    font-size: 1rem;
  }
}
</style>