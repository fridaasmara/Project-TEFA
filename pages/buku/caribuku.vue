<template>
  <div class="container-fluid pt-2 pb-5">
    <div class="text-center text-dark">
      <h3>Cari Buku</h3>
    </div>
    <div class="row mt-5 mb-3 p-2 d-flex justify-content-center">
      <div class="col-md-8 mb-2">
        <form @submit.prevent="getBooks" class="input-group flex-nowrap rounded">
          <input v-model="keyword" type="search" class="form-control" placeholder="Cari buku" aria-label="Search"
            aria-describedby="search-addon" />
          <span class="input-group-text"><i class="bi bi-search"></i></span>
        </form>
      </div>
      <div class="col-md-3">
        <select v-model="keyword" class="form-control form-select" id="keanggotaan">
          <option value="">Kategori</option>
          <option v-for="(kategori, i) in kategoris" :key="kategori.id" :value="kategori.nama">{{ kategori.nama }}
          </option>
        </select>
      </div>
    </div>
    <div class="row mt-4 p-3">
      <div class="col">
        <div class="rekomen text-dark">Rekomendasi</div>
        <p class="mt-3 text-muted p-3">Menampilkan : {{ bookFiltered.length }} dari {{ jmlBuku }} buku</p>
      </div>
      <div class="col text-end">
        <nuxt-link to="/">
          <button class="btn btn-primary first"><i class="bi bi-house-door-fill"></i></button>
        </nuxt-link>

        <nuxt-link to="../pengunjung/tambah">
          <button class="btn btn-primary">Kunjungan</button>
        </nuxt-link>
      </div>
    </div>

    <div class="row gy-5 my-3 cardbook p-4 bg-white rounded shadow">
      <div v-for="(book, i) in bookFiltered" :key="i" class="col-sm-6 col-md-4 col-lg-2 d-flex">
        <div class="card flex-fill">
          <img :src="book.cover" class="card-img-top" alt="img-cover">
          <div class="card-body">
            <div class="text-center">
              <button class="btn btn-primary my-2 center" data-bs-toggle="modal"
                :data-bs-target="`#buku-${book.id}`">Lihat Detail </button>
            </div>

            <div class="modal fade" :id="`buku-${book.id}`">
              <div class="modal-dialog modal-dialog-centered modal-lg">
                <div class="modal-content rounded-4">
                  <div class="modal-header">
                    <h4 class="modal-title fw-bold" id="detailbukuModalLabel">{{ book.judul }}</h4>
                    <button type="button" class="btn-close" data-bs-dismiss="modal" aria-label="Close"></button>
                  </div>
                  <div class="modal-body">
                    <div class="row">
                      <div class="col-md-3">
                        <img :src="book.cover" class="img-fluid">
                      </div>
                      <div class="col-md">
                        <ul class="list-group">
                          <li class="list-group-item"><strong>Penulis :</strong> {{ book.penulis }}</li>
                          <li class="list-group-item"><strong>Penerbit :</strong> {{ book.penerbit }}</li>
                          <li class="list-group-item"><strong>Tahun Terbit :</strong> {{ book.tahun_terbit }}</li>
                          <li class="list-group-item"><strong>Sinopsis :</strong> {{ book.sinopsis }}</li>
                          <li class="list-group-item"><strong>Kategori :</strong> {{ book.kategori?.nama }}</li>
                          <li class="list-group-item"><strong>Rak :</strong> {{ book.rak }}</li>
                        </ul>
                      </div>
                    </div>
                  </div>
                  <div class="modal-footer">
                    <button type="button" class="btn text-light" data-bs-dismiss="modal">Tutup</button>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>


<script setup>
useHead({ title: "Perpus Digital - Buku" })

const supabase = useSupabaseClient()
const kategoris = ref([])
const books = ref([])
const jmlBuku = ref(0)
const keyword = ref('')

const getBooks = async () => {
  const { data, error } = await supabase.from('buku').select(`*, kategori(*)`)
    .ilike('judul', `%${keyword.value}%`)
  if (data) {
    books.value = data
    data.forEach(book => {
      const { data } = supabase.storage.from('coverbuku').getPublicUrl(book.cover)
      if (data) {
        book.cover = data.publicUrl
      }
    })
  }
}


const getKategori = async () => {
  const { data, error } = await supabase.from('kategori_buku').select()
  if (data) kategoris.value = data
}

const bookFiltered = computed(() => {
  return books.value.filter((b) => {
    return (
      b.judul?.toLowerCase().includes(keyword.value.toLowerCase()) ||
      b.kategori?.nama.toLowerCase().includes(keyword.value.toLowerCase())
    )
  })
})

const getjmlBuku = async () => {
  const { data, count } = await supabase
    .from('buku')
    .select('*', { count: 'exact' })
  if (data) jmlBuku.value = count
}

onMounted(() => {
  getBooks()
  getKategori()
  getjmlBuku()
})


</script>


<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Poppins:ital,wght@0,100;0,200;0,300;0,400;0,500;0,600;0,700;0,800;0,900;1,100;1,200;1,300;1,400;1,500;1,600;1,700;1,800;1,900&display=swap');

h3,
input,
select,
option,
.rekomen,
.text-muted,
.btn,
.modal {
  font-family: "Poppins", sans-serif;
}

.input-group-text {
  background-color: #fffF;
  border-left: none !important;
}

.form-control {
  border-right: none;
}


h3 {
  margin-top: 225px;
}

.rekomen {
  font-size: 25px;
  margin-left: 25px;
}

.btn {
  background-color: #394367 !important;
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

.first {
  margin-right: 2rem;
}

.text-end {
  margin-right: 2rem;
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
    margin-right: 0.7em;
  }

  .first {
    margin-bottom: 5px;
    margin-left: 20px;
  }

  .modal {
    padding: 2em;
    font-size: small;
  }

  .modal-title {
    font-size: small;
  }

  .card {
    width: 100%;
    height: 27rem;
  }

  h5 {
    font-size: 1rem;
  }
}

@media only screen and (min-width: 884px) and (max-width: 1280px) {
  .card {
    height: 22rem;
  }
}
</style>