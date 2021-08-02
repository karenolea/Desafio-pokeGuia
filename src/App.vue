<template>
  <div id="app">
    <img alt="pokemonSeleccionado" src="./assets/image.png" />
    <h1>PokeGuía</h1>

    <form>
      <div>
        <label for="">Nombre: </label>
        <input v-model="pokemon.name" />
        <button @click.prevent="btn">Buscar</button>
      </div>
    </form>
    <pokemonSeleccionado :pokemon="this.pokemon"></pokemonSeleccionado>
  </div>
</template>

<script>
import PokemonSeleccionado from "./components/PokemonSeleccionado.vue";

export default {
  name: "App",
  components: {
    PokemonSeleccionado,
  },
  data() {
    return {
      pokemon: {
        name: "pikachu",
        sprites: {
          front_default: "",
        },
        moves: [],
        abilities: [],
      },
    }
  },
  created() {
    this.btn();
  },
  methods: {
    btn() {
      fetch(`https://pokeapi.co/api/v2/pokemon/${this.pokemon.name}`)
        .then((response) => response.json())
        .then((json) => (this.pokemon = json));
     
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
img {
  width: 30%;
}
h1 {
  font-size: 3rem;
}
</style>
