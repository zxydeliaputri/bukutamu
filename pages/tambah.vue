<template>
      <div>
            <h1>Isi Buku Tamu</h1>
            <form @submit.prevent="simpan()">
                  <input v-model="nama" placeholder="nama"> <br/>
                  <input v-model="instansi" placeholder="instansi"> <br/>
                  <textarea v-model="alamat" placeholder="alamat"></textarea> <br/>
                  <button type="submit">Kirim</button>
                  <NuxtLink to="/">Kembali</NuxtLink>
            </form>
      </div>
</template>

<script setup>
      const supabase = useSupabaseClient()
      const nama = ref()
      const instansi = ref()
      const alamat = ref()

      async function simpan() {
            await supabase
            .from("pengunjung")
            .insert({
                  nama: nama.value,
                  instansi: instansi.value,
                  alamat: alamat.value,
            })
            navigateTo("/")
      }
</script>