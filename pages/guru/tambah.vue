<template>
  <div class="container-fluid">
    <div class="row">
      <div class="col-lg-12">
        <h2 class="text-center my-4">ISI KEHADIRAN</h2>
        <form @submit.prevent="kirimData">
          <div class="mb-3">
            <select 
            v-model="form.nama"
            class="form-control form-control-lg form-select rounded-5">
          <option value="">Nama</option>
          <option v-for="(siswa, i) in objec" :key="i" :value="siswa.id">{{ siswa.nama }}</option>
          </select>
          </div>
          <!-- <div class="mb-3">
            <select 
                 v-model="form.siswa" control
                 class="form-control form--lg form-select rounded-5">
              <option>NAMA</option>
              <option v-for="(siswa, i) in objec" :key="i" :value="siswa.id">{{ siswa.nama }}</option>
            </select>
          </div> -->
          <div class="mb-3">
            <select v-model="form.nama" 
            class="form-control form-control-lg form-select rounded-5">
              <option value="">keterangan</option>
              <option v-for="(keterangan, i) in objectives" :key="i" :value="keterangan.id">{{ keterangan.nama }}</option>
            </select>
          </div>
          <div class="mb-3">
            <input v-model="form.alasan" type="text" class="form-control form-control-lg rounded-5"
              placeholder="Alasan...">
          </div>
          <div class="d-flex justify-content-between">
            <nuxt-link to="/siswa" class="btn btn-primary btn-lg rounded-5 px-5">Kirim</nuxt-link>

            <nuxt-link to="/home" class="btn btn-danger btn-lg rounded-5 px-5">
              back
            </nuxt-link>
          </div>


        </form>
      </div>
    </div>
  </div>
</template>

<script setup>
const supabase = useSupabaseClient()

const members = ref([])
const objectives = ref([])
const objec = ref([])


const form = ref({
  nama: "",
  keterangan: "",
  alasan: "",
})
const kirimData = async () => {
  const { error } = await supabase.from('form_guru').insert([form.value])
  if (!error) navigateTo('/guru')
  console.log(form.value)
}

const getKeterangan = async () => {
  const { data } = await supabase.from( 'keterangan').select('*')
  if (data) objectives.value = data
}
const getSiswa = async () => {
  const { data, error } = await supabase.from( 'siswa').select('*')
  if (data) objec.value = data
}
onMounted(() => {
  getKeterangan()
  getSiswa()
})

</script>