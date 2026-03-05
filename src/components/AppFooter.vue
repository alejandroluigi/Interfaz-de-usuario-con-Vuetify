<template>
  <v-footer color="grey-darken-3" class="text-white">
    <v-container>
      <v-row>

        <!-- Datos del estudiante -->
        <v-col cols="12" md="6">
          <p><strong>Nombre:</strong> Alejandro López Meza</p>
          <p><strong>Matrícula:</strong> 1184506</p>
        </v-col>

        <!-- Información adicional -->
        <v-col cols="12" md="6" class="text-md-right">
          <p><strong>Fecha:</strong> {{ fechaActual }}</p>
          <p>© {{ year }} - Mi Portafolio Fotográfico</p>
          <p>Contacto: alejandro.lopez@uabc.edu.mx</p>
        </v-col>

      </v-row>
    </v-container>
  </v-footer>
</template>

<script>
export default {
  name: "AppFooter",
  data() {
    return {
      fechaActual: "",
      year: new Date().getFullYear()
    }
  },
  mounted() {
    const hoy = new Date()
    this.fechaActual = hoy.toLocaleDateString("es-MX", {
      weekday: "long",
      year: "numeric",
      month: "long",
      day: "numeric"
    })
  }
}
</script>