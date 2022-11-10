<template>
  <div
    class="p-1 flex items-center rounded-lg border max-w-xl border-orange-700 bg-gray-700 hover:bg-gray-900"
  >
    <img class="max-w-xs h-" :src="personaje.img" alt="" />
    <div class="">
      <div>
        <h5 class="mb-2 text-2xl text-white">
          {{ personaje.name }}
        </h5>
        <p class="font-normal text-white">
          <b>Profesions: </b> {{ personaje.occupation[0] }} <br />
          {{ personaje.occupation[1] }}
        </p>
      </div>
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
