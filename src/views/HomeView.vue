<template>
  <div class="hello">
    <h1 class="text-3xl font-bold underline">Os 151 Pokémon's</h1>
    <div
      class="p-10 grid grid-cols-1 sm:grid-cols-1 md:grid-cols-3 lg:grid-cols-3 xl:grid-cols-3 gap-5"
    >
      <div
        v-for="(item, index) in pokemon"
        :key="item.name"
        class="max-w-sm rounded overflow-hidden shadow-lg"
      >
        <img
          class="w-full"
          v-bind:src="sprite + (index = index + 1) + '.png'"
          alt="Pokémon"
        />
        <div class="px-6 py-4">
          <div class="font-bold text-xl mb-2">
            {{ item.name.toUpperCase() }}
          </div>
          <p class="text-gray-700 text-base">
            <router-link :to="{ name: 'pokemon', params: { id: index } }"
              >Detalhes</router-link
            >
          </p>
        </div>
        <div class="px-6 pt-4 pb-2">
          <span
            class="inline-block bg-gray-200 rounded-full px-3 py-1 text-sm font-semibold text-gray-700 mr-2 mb-2"
            >#photography</span
          >
          <span
            class="inline-block bg-gray-200 rounded-full px-3 py-1 text-sm font-semibold text-gray-700 mr-2 mb-2"
            >#travel</span
          >
          <span
            class="inline-block bg-gray-200 rounded-full px-3 py-1 text-sm font-semibold text-gray-700 mr-2 mb-2"
            >#winter</span
          >
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";
export default {
  name: "HelloWorld",

  data() {
    return {
      pokemon: null,
      sprite:
        "https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/versions/generation-viii/icons/",
    };
  },
  mounted() {
    axios
      .get("https://pokeapi.co/api/v2/pokemon?limit=151&offset=0")
      .then((response) => (this.pokemon = response.data.results));
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
