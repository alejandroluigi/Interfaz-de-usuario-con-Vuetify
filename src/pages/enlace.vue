<template>
  <AppHeader />

  <v-container class="mt-6">

    <!-- ALERTA DE ERROR -->
    <v-alert
      v-if="error"
      type="error"
      class="mb-4"
      dismissible
    >
      {{ error }}
    </v-alert>

    <!-- TARJETAS -->
    <v-row>
      <v-col cols="12" md="6">
        <TarjetaConImagen
          :imageUrl="card1.imageUrl"
          :title="card1.title"
          :description="card1.description"
          :author="card1.author"
        />
      </v-col>

      <v-col cols="12" md="6">
        <TarjetaConImagen
          :imageUrl="card2.imageUrl"
          :title="card2.title"
          :description="card2.description"
          :author="card2.author"
        />
      </v-col>
    </v-row>

    <!-- BOTÓN DE ACTUALIZACIÓN -->
    <v-row class="my-6">
      <v-col class="text-center">
        <v-btn
          color="primary"
          :loading="loading"
          :disabled="loading"
          @click="actualizarImagenes"
        >
          Actualizar Imágenes
        </v-btn>
      </v-col>
    </v-row>

    <!-- TABLA -->
    <TablaDeDatos />

  </v-container>

  <AppFooter />
</template>

<script lang="ts" setup>
import { ref, onMounted } from 'vue'
import AppHeader from '@/components/AppHeader.vue'
import AppFooter from '@/components/AppFooter.vue'
import TarjetaConImagen from '@/components/TarjetaConImagen.vue'
import TablaDeDatos from '@/components/TablaDeDatos.vue'

const loading = ref(false)
const error = ref('')

const card1 = ref({
  imageUrl: '',
  title: 'Fotografía 1',
  description: 'Imagen aleatoria obtenida desde Picsum.',
  author: ''
})

const card2 = ref({
  imageUrl: '',
  title: 'Fotografía 2',
  description: 'Imagen aleatoria obtenida desde Picsum.',
  author: ''
})

const actualizarImagenes = async () => {
  loading.value = true
  error.value = ''

  try {
    const response = await fetch(
      'https://picsum.photos/v2/list?page=1&limit=50'
    )

    if (!response.ok) {
      throw new Error('Error en la respuesta del servidor')
    }

    const data = await response.json()

    // Elegir dos imágenes diferentes
    const random1 = Math.floor(Math.random() * data.length)
    let random2 = Math.floor(Math.random() * data.length)

    while (random2 === random1) {
      random2 = Math.floor(Math.random() * data.length)
    }

    const img1 = data[random1]
    const img2 = data[random2]

    card1.value = {
      imageUrl: `https://picsum.photos/id/${img1.id}/300/200`,
      title: `Imagen ID ${img1.id}`,
      description: 'Fotografía aleatoria obtenida desde la API.',
      author: img1.author
    }

    card2.value = {
      imageUrl: `https://picsum.photos/id/${img2.id}/300/200`,
      title: `Imagen ID ${img2.id}`,
      description: 'Fotografía aleatoria obtenida desde la API.',
      author: img2.author
    }

  } catch (err) {
    error.value = 'Ocurrió un error al obtener las imágenes. Intenta nuevamente.'
  } finally {
    loading.value = false
  }
}

// Cargar imágenes al iniciar la página
onMounted(() => {
  actualizarImagenes()
})
</script>