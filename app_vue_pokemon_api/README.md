# Adivina el Pokémon

Este proyecto es una aplicación interactiva basada en la temática de Pokémon, donde el usuario debe adivinar el nombre de los Pokémon solo viendo su silueta. El objetivo es revelar los Pokémon ocultos al acertar sus nombres.

## Descripción

Al cargar la aplicación, se seleccionan 20 Pokémon de la PokéAPI de forma aleatoria. La interfaz muestra la imagen de cada Pokémon con un filtro que oculta su apariencia, y el usuario tiene un campo de entrada para intentar adivinar el nombre. Cuando el usuario acierta el nombre, el Pokémon se revela y se incrementa el contador de "Pokémon descubiertos".

La aplicación está diseñada para probar conocimientos de Vue.js y el consumo de APIs.

## Características

- **Consumo de API**: Se utiliza la PokéAPI para obtener una lista completa de Pokémon y seleccionar 20 de forma aleatoria.
- **Interacción**: El usuario ingresa el nombre de un Pokémon debajo de cada imagen. Si es correcto, la imagen se muestra sin filtro.
- **Contador**: Se mantiene un contador de Pokémon descubiertos.
- **Lista de Nombres para Pruebas**: Incluye un componente para mostrar los nombres correctos en JSON, útil para testing.

## Tecnologías Utilizadas

- **Vue.js**: Framework principal para la interfaz de usuario.
- **Bootstrap**: Para el diseño y estilos responsivos.
- **Axios**: Para el consumo de la API.
- **PokéAPI**: API pública utilizada para obtener los datos de los Pokémon.

## Requisitos

Asegúrate de tener instalado:

- Node.js (v14 o superior)
- npm (gestor de paquetes de Node)

## Instalación

1. Clona el repositorio:

   ```bash
   git clone https://github.com/maaferna/DesafioLatamM7Prueba1VUE.git
   ```

Navega al directorio del proyecto:
```bash
   cd app_vue_pokemon_api
```

Instala las dependencias:

```bash
npm install
```

Inicia el servidor de desarrollo:

```bash
npm run dev
```

Abre tu navegador y ve a http://localhost:5173 para ver la aplicación en funcionamiento.


## Estructura del Proyecto

App.vue: Componente principal que carga HomeView.

HomeView.vue: Vista principal que contiene el título, contador de Pokémon descubiertos, y lista de Pokémon.

PokemonItem.vue: Componente hijo que muestra cada Pokémon y su campo de entrada.

PokemonListTester.vue: Componente adicional para mostrar los nombres correctos en formato JSON.

adivina-el-pokemon/
├── public/
│   ├── favicon.ico
│   └── index.html
├── src/
│   ├── assets/
│   │   └── img/
│   │       └── logo.png          # Logo del proyecto
│   ├── components/
│   │   ├── PokemonItem.vue        # Componente individual para mostrar cada Pokémon
│   │   └── PokemonListTester.vue  # Componente opcional para pruebas (lista en JSON de nombres correctos)
│   ├── views/
│   │   └── HomeView.vue           # Vista principal de la aplicación
│   ├── App.vue                    # Componente raíz de la aplicación
│   ├── main.js                    # Archivo principal de JavaScript para montar la app
│   └── router/
│       └── index.js               # Configuración de rutas de Vue Router
├── package.json                   # Dependencias y scripts del proyecto
└── README.md                      # Documentación del proyecto



## Ciclo de Vida del Componente

En el created hook de HomeView.vue, se llama a fetchAllPokemons() para obtener todos los Pokémon de la API y seleccionar 20 al azar para mostrar.

### Funcionalidades Principales

1. Adivina el Nombre del Pokémon
Cada imagen de Pokémon tiene un campo de entrada. El usuario debe ingresar el nombre correcto para revelar la imagen.

2. Contador de Pokémon Descubiertos
Cada vez que un Pokémon se descubre, el contador incrementa en uno.

3. Mostrar Nombres para Pruebas
El componente PokemonListTester.vue permite mostrar un listado en JSON de los nombres correctos para testing.

### Ejemplo de Uso

Al cargar la aplicación, se mostrarán 20 Pokémon con sus imágenes ocultas.
Escribe el nombre del Pokémon en el campo correspondiente y presiona Enter o el botón "Descubrir".

Si el nombre es correcto, la imagen se revelará y el contador de Pokémon descubiertos aumentará.

Puedes activar el componente PokemonListTester para ver los nombres correctos.

