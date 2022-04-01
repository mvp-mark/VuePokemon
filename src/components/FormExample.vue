<template>
  <form v-on:submit.prevent="submitForm">
    <div class="flex flex-col justify-center items-center">
      <input
        v-model="form.name"
        class="input max-w-sm border rounded-sm m-2 p-2"
        type="text"
        placeholder="Nome"
      />
      <input
        v-model="form.email"
        class="input max-w-sm border rounded-sm m-2 p-2"
        type="email"
        placeholder="Email"
      />
      <input
        v-model="form.gender"
        class="input max-w-sm border rounded-sm m-2 p-2"
        type="text"
        placeholder="Genero"
      />
      <input
        v-model="form.status"
        class="input max-w-sm border rounded-sm m-2 p-2"
        type="text"
        placeholder="Status"
      />
    </div>
    <button class="input max-w-sm border rounded-sm m-2 p-2 font-extrabold">
      Enviar
    </button>
  </form>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import axios from "axios";
export default defineComponent({
  name: "FormExample",
  data() {
    return {
      form: {
        name: "",
        email: "",
        gender: "",
        status: "",
      },
    };
  },
  methods: {
    submitForm() {
      axios
        .post("https://gorest.co.in/public/v2/users", this.form, {
          headers: {
            Authorization:
              "Bearer 8627d328665f488d66b959e4491ef7cc090699146e3d03a09108b476b33e1689",
          },
        })
        .then((response) => console.log(response));
    },
  },
});
</script>
