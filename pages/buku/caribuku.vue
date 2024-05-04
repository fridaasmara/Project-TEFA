<template>
  <div class="container-fluid pt-2 pb-5">
    <div class="text-center text-dark">
      <h3>Cari Buku</h3>
    </div>
    <div class="row mt-5 mb-3 p-2 d-flex justify-content-center">
      <div class="col-md-8 mb-2">
        <form @submit.prevent="getBooks" class="input-group flex-nowrap rounded">
          <input v-model="keyword" type="search" class="form-control" placeholder="Cari buku" aria-label="Search" aria-describedby="search-addon"/>
          <span class="input-group-text"><i class="bi bi-search"></i></span> 
        </form>
      </div>
      <div class="col-md-3">
        <select v-model="keyword" class="form-control form-select" id="keanggotaan">
          <option value="">Kategori</option>
          <option v-for="(kategori, i) in kategoris" :key="kategori.id" :value="kategori.nama">{{ kategori.nama }}</option>
        </select>
      </div>
    </div>
    <div class="row mt-4 p-3">
      <div class="col">
        <div class="rekomen text-dark">Rekomendasi</div>
        <h5 class="mt-3 text-dark disabled p-3">Menampilkan : {{ books.length }} buku</h5>
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

    <div class="row gy-5 my-3 cardbook p-4 bg-white rounded shadow">
      <div v-for="(book, i) in bookFiltered" :key="i"  class="col-sm-6 col-md-4 col-lg-2">
        <div class="card">
          <img :src="book.cover" class="card-img-top" alt="img-cover">
          <div class="card-body">
            <div class="text-center">
              <button class="btn btn-primary my-2 center" data-bs-toggle="modal" :data-bs-target="`#buku-${book.id}`">Lihat Detail </button>
            </div>

            <div class="modal fade" :id="`buku-${book.id}`">                                                                           
              <div class="modal-dialog modal-dialog-centered modal-lg">
                <div class="modal-content rounded-4">
                  <div class="modal-header  text-center">
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
                                    <li class="list-group-item"><strong>Penulis :</strong> {{ book.penulis }}s</li>
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
                    <button type="button" class="btn text-light" data-bs-dismiss="modal">Close</button>
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
const supabase = useSupabaseClient()
const kategoris = ref ([])
const books = ref([])

const keyword = ref('')

const getBooks = async () => {
  const { data, error } = await supabase.from('buku').select(`*, kategori(*)`)
  .ilike('judul', `%${keyword.value}`)
  if(data) {
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
  if(data) kategoris.value = data
}

const bookFiltered = computed (() => {
  return books.value.filter((b) => {
    return (
      b.judul?.toLowerCase().includes(keyword.value.toLowerCase()) || 
      b.kategori?.nama.toLowerCase().includes(keyword.value.toLowerCase())
    )
  })
})

onMounted(() => {
  getBooks()
  getKategori()
})


</script>


<style scoped>
.input-group-text {
  background-color: #fff;
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
  height: 24rem;
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
    margin-left: 1rem;
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

</style>