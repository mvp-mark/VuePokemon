<template>
  <div class="hello">
    <h1 class="text-3xl font-bold underline">{{ msg }}</h1>
    <div class="">
      <div
        v-for="(item, index) in pokemon"
        :key="item.name"
        class="card m-4 p-4 flex justify-center flex-justify flex-row"
        style="width: 18rem"
      >
        <div class="card-body">
          <div class="max-w-sm rounded overflow-hidden shadow-lg">
            <img
              class="w-full"
              v-bind:src="sprite + (index = index + 1) + '.png'"
              alt="Pokémon"
            />
            <div class="px-6 py-4">
              <div class="font-bold text-xl mb-2">
                {{ item.name.toUpperCase() }}
              </div>
              <p class="text-gray-700 text-base">Lorem ipsum dolor sit amet</p>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";
export default {
  name: "HelloWorld",
  props: {
    msg: String,
  },
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
