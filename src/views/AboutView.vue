<template>
  <div>
    <h2 class="text-center font-semibold underline-offset-8">
      {{ pokemon?.name.toUpperCase() }}
    </h2>
  </div>

  <FormExample />
</template>

<script>
import axios from "axios";
import FormExample from "@/components/FormExample.vue";
export default {
  name: "PokemonId",
  components: {
    FormExample,
  },

  created() {
    this.$watch(
      () => this.$route.params,
      (toParams, previousParams) => {
        // react to route changes...
      }
    );
  },
  data() {
    return {
      pokemon: null,
    };
  },

  mounted() {
    axios
      .get(`https://pokeapi.co/api/v2/pokemon/${this.$route.params.id}`)
      .then((response) => {
        this.pokemon = response.data;
        console.table("Pokemon", this.pokemon);
        console.log("ID", this.$route.params.id);
        // console.log("img?", this?.pokemon.sprites.front_default);
      });
  },
};
</script>
