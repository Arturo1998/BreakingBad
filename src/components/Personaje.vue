<template>
  <div
    class="p-1 flex flex-nowrap rounded-lg md:text-sm border border-orange-700 bg-gray-700 hover:bg-gray-900"
  >
    <div class="">
      <img class="max-h-72 rounded-lg" :src="personaje.img" alt="" />
    </div>
    <div class="ml-10 w-96">
      <h5 class="text-base font-['Roboto'] text-white font mt-4">
        {{ personaje.name }}
      </h5>

      <p class="font-normal text-white text-xs">
        <b>Profesions: </b>
        <br />
        {{ personaje.occupation[0] }}
        <br />
        {{ personaje.occupation[1] }}
      </p>
      <div class="mt-2">
        <p class="text-white text-xs">
          <b>Cumpleaños:</b>
          <br />
          {{ personaje.birthday }}
        </p>
      </div>
    </div>
    <div class="mt-3">
      <button
        class="text-white rounded bg-gray-500 py-2 px-4 border border-orange-700 mt-12"
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
