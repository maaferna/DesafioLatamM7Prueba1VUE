<template>
  <div class="container mt-5">
    <img class="d-block mx-auto" src="https://raw.githubusercontent.com/PokeAPI/media/master/logo/pokeapi_256.png" alt="logo pokeapi">
    <h1 class="text-center">Adivina el Pokémon</h1>
    <p class="text-center">Adivina el nombre de cada Pokémon para descubrirlo.</p>
    
    <!-- Contador de Pokémon descubiertos -->
    <h3 class="text-center">Pokémon descubiertos: {{ discoveredCount }}</h3>

    <!-- Renderiza la lista de Pokémon -->
    <div class="row">
      <div class="col-md-3 mb-4" v-for="(pokemon, index) in selectedPokemons" :key="index">
        <PokemonItem :pokemon="pokemon" :allPokemonNames="allPokemonNames" @pokemonDiscovered="incrementDiscoveredCount" />
      </div>
    </div>

    <!-- Mostrar listado en JSON format para testear el funcionamiento -->
    <PokemonListTester :correctAnswers="selectedPokemons.map(pokemon => pokemon.name)" />
  </div>
</template>

<script>
import axios from 'axios';
import PokemonItem from '../components/PokemonItem.vue';
import PokemonListTester from '../components/PokemonListTester.vue';

export default {
  components: {
    PokemonItem,
    PokemonListTester
  },
  data() {
    return {
      allPokemonNames: [],
      selectedPokemons: [],
      discoveredCount: 0,
    };
  },
  created() {
    this.fetchAllPokemons();
  },
  methods: {
    async fetchAllPokemons() {
      try {
        const response = await axios.get('https://pokeapi.co/api/v2/pokemon?limit=1000');
        this.allPokemonNames = response.data.results.map(pokemon => pokemon.name).sort();

        const randomIds = this.getRandomIds(this.allPokemonNames.length, 20);

        const pokemonPromises = randomIds.map(id => axios.get(`https://pokeapi.co/api/v2/pokemon/${id}`));
        const pokemonData = await Promise.all(pokemonPromises);

        this.selectedPokemons = pokemonData.map(pokemon => ({
          id: pokemon.data.id,
          name: pokemon.data.name,
          image: pokemon.data.sprites.front_default,
          discovered: false,
          guessedName: ''
        }));
      } catch (error) {
        console.error("Error fetching Pokémon data:", error);
      }
    },
    getRandomIds(max, count) {
      const ids = new Set();
      while (ids.size < count) {
        ids.add(Math.floor(Math.random() * max) + 1);
      }
      return Array.from(ids);
    },
    incrementDiscoveredCount() {
      this.discoveredCount++;
    }
  }
};
</script>

<style scoped>

</style>
