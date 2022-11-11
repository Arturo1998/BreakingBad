<template>
  <div
    class="p-1 grid grid-cols-3 rounded-lg border border-orange-700 bg-gray-700 hover:bg-gray-900"
  >
    <div class="">
      <img class="h-72" :src="personaje.img" alt="" />
    </div>
    <div class="ml-10 w-96">
      <h5 class="text-2xl font-['Roboto'] text-white font mt-10">
        {{ personaje.name }}
      </h5>

      <p class="font-normal text-white">
        <b>Profesions: </b>
        <br />
        {{ personaje.occupation[0] }}
        <br />
        {{ personaje.occupation[1] }}
      </p>
    </div>
    <div class="mt-56">
      <button
        class="text-white rounded bg-gray-500 py-2 px-4 border border-orange-700 mt-3"
        @click="enviarFav"
      >
        ❤️
      </button>
    </div>
  </div>
</template>

<script lang="js">
export default {
  name: "ListaPersonajes",
  props: {
    personaje: {
      type: Object,
    },
  },
  emits: ["enviarFav"],
  methods: {
    enviarFav() {
      this.$emit("enviarFav", this.personaje);
      console.log("enviando desde personaje...")
    },
  },
};
</script>

<style scoped></style>
