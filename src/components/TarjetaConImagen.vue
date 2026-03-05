<template>
  <v-card class="mx-auto my-4" max-width="400" elevation="4">

    <!-- Imagen desde Picsum -->
    <v-img
      :src="imageUrl"
      height="250"
      cover
    ></v-img>

    <!-- Contenido -->
    <v-card-title>
      {{ title }}
    </v-card-title>

    <v-card-subtitle>
      Autor: {{ author }}
    </v-card-subtitle>

    <v-card-text>
      {{ description }}
    </v-card-text>

  </v-card>
</template>

<script lang="ts" setup>
defineProps<{
  imageUrl: string
  title: string
  description: string
  author: string
}>()
</script>