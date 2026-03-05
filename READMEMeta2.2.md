## Meta 2.2 - Interfaz de usuario con Vuetify

# Descripción del Proyecto

Aplicación web desarrollada con Vue 3 + Vuetify 3 + TypeScript, que muestra un portafolio fotográfico dinámico.

La aplicación incluye:

- Barra de navegación (AppHeader)
- Tarjetas reutilizables con imágenes obtenidas desde la API de Picsum
- Botón para actualizar imágenes dinámicamente
- Tabla con información del perfil del estudiante
- Pie de página con datos académicos y fecha dinámica
- Aplicacion central en donde estan los 4 componentes (pages/inlace.vue)

El proyecto demuestra el uso de componentes reutilizables, consumo de API externa, manejo de estado y diseño responsive con Vuetify.

# Captura de Pantalla

capturas de pantalla del proyecto funcionando.

Ejemplo 1:

![Portafolio fotográfico de Vuetify mostrando interfaz con encabezado azul, dos tarjetas con imágenes aleatorias de Picsum, información del autor, y botón Actualizar Imágenes en fondo oscuro](./public/meta%202.2%20Ejemplo%20de%20ejecucion%201.png)

Ejemplo 2:
![Portafolio fotográfico de Vuetify mostrando interfaz con encabezado azul, dos tarjetas con imágenes aleatorias de Picsum, información del autor, y botón Actualizar Imágenes en fondo oscuro](./public/meta%202.2%20Ejemplo%20de%20ejecucion%202.png)

Guarda la imagen dentro del proyecto (por ejemplo en /public) y ajusta la ruta si es necesario.

# Instrucciones de Instalación y Ejecución
1️. Clonar el repositorio
git clone https://github.com/alejandroluigi/Interfaz-de-usuario-con-Vuetify
cd tu-repositorio

2️. Instalar dependencias

npm install

3️. Ejecutar el proyecto en modo desarrollo

npm run dev

# Tecnologías Utilizadas

- Vue 3
- Vuetify 3
- TypeScript
- Vite
- Fetch API
- Picsum Photos API

# Estructura del Proyecto
vuetify_proyecto/
│
├── public/
├── src/
│   ├── assets/
│   ├── components/
│   │   ├── AppHeader.vue
│   │   ├── AppFooter.vue
│   │   ├── TarjetaConImagen.vue
│   │   ├── TablaDeDatos.vue
│   │   └── MiComponente.vue
│   │
│   ├── pages/
│   │   ├── index.vue
│   │   └── enlace.vue
│   │
│   ├── plugins/
│   ├── router/
│   ├── App.vue
│   ├── main.ts
│   └── env.d.ts
│
├── package.json
└── README.md


# Funcionamiento de la Integración con la API

La aplicación consume la API pública de Picsum Photos para obtener imágenes aleatorias.

Endpoint utilizado:
GET https://picsum.photos/v2/list?page=1&limit=50

Este endpoint devuelve una lista de imágenes con los siguientes datos:

- id
- author
- width
- height
- download_url

# Proceso de funcionamiento:

Al presionar el botón "Actualizar Imágenes", se ejecuta una función asíncrona.

Se realiza una petición fetch al endpoint de Picsum.

Se seleccionan dos imágenes aleatorias diferentes.

Se construyen las URLs usando el formato:

https://picsum.photos/id/{id}/300/200

Se actualizan las tarjetas con:

- Nueva imagen
- ID como título
- Nombre del autor en el subtítulo

Mientras se realiza la petición:

El botón muestra estado loading

Se deshabilita para evitar múltiples peticiones

En caso de error de red:

Se muestra un mensaje usando v-alert