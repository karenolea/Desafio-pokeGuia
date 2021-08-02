<template>
  <div id="app1">
    <img :src=imagenes alt="pokemon" />

    <h2>Movimientos</h2>
    <ul>
      <li v-for="(dato, index) in movimientos" :key="index">
        {{ dato.move.name }}
      </li>
    </ul>

    <h2>Habilidades</h2>
    <ul>
      <li v-for="(dato, index) in habilidades" :key="index">
        {{ dato.ability.name }}
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: "PokemonSeleccionado",
  props: {
    pokemon: [],
  },
  computed: {
    imagenes() {
      return this.pokemon.sprites.front_default
    },
    habilidades() {
      return this.pokemon.abilities
    },
    movimientos() {
      return this.pokemon.moves
    },
    
  },
};
</script>
<style scoped>
.li {
  text-align: center;
}
img {
  width: 13%;
}
ul {
  list-style: none;
  text-align: center;
}
</style>