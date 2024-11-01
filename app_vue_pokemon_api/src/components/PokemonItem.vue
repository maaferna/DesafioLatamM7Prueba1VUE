<template>
    <div class="pokemon-item card text-center p-3 mb-3">
      <img
        :src="pokemon.image"
        :class="{ 'blurred': !isDiscovered, 'revealed': isDiscovered }"
        alt="Imagen del Pokémon"
      />
      <div v-if="!isDiscovered">
        <select v-model="guessedName" class="form-control my-2">
          <option disabled value="">Selecciona el nombre del Pokémon</option>
          <option v-for="name in allPokemonNames" :key="name">{{ name }}</option>
        </select>
        <button @click="checkGuess" class="btn btn-primary">Descubrir</button>
      </div>
      <div v-else>
        <h4>{{ pokemon.name }}</h4>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    props: {
      pokemon: Object,
      allPokemonNames: Array
    },
    data() {
      return {
        guessedName: '',
        isDiscovered: false 
      };
    },
    methods: {
      checkGuess() {
        if (this.guessedName.toLowerCase() === this.pokemon.name.toLowerCase()) {
          this.isDiscovered = true;
          this.$emit('pokemonDiscovered'); 
        } else {
          alert('Nombre incorrecto, intenta de nuevo.');
        }
      }
    }
  };
  </script>
  
  <style scoped>
  .blurred {
    filter: blur(5px);
  }
  .revealed {
    filter: none;
  }
  </style>
  
