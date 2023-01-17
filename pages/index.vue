<template>
      <div>
            <h1>Pengunjung</h1>
            <NuxtLink to="/tambah">Isi Buku</NuxtLink>
            <table border="1" width="50%">
                  <thead>
                        <tr>
                              <th>#</th>
                              <th>NAMA</th>
                              <th>INSTANSI</th>
                              <th>ALAMAT</th>
                        </tr>
                  </thead>
                  <tbody>
                        <tr v-for="visitor in datas" :key="visitor.id">
                              <td>{{ visitor.id }}</td>
                              <td>{{ visitor.nama }}</td>
                              <td>{{ visitor.instansi }}</td>
                              <td>{{ visitor.alamat }}</td>
                        </tr>
                  </tbody>
            </table>
      
      </div>
</template>

<script setup>
      const supabase = useSupabaseClient()
      const datas = ref([])

      async function getData() {
            const { data, error } = await supabase
            .from("pengunjung")
            .select()
            datas.value = data
      }

      onMounted(() => {
            getData()
      })
</script>