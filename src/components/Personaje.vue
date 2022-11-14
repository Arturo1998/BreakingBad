<template>
  <div
    class="p-1 min-h-72 flex flex-row rounded-lg text-lg border border-orange-700 bg-gray-700 hover:bg-gray-900"
  >
    <div class="flex mr-10">
      <img class="max-h-72 rounded-lg" :src="personaje.img" alt="" />
    </div>
    <div class="m-auto">
      <h5 class="text-xl font-['Roboto'] text-white font mt-4">
        {{ personaje.name }}
      </h5>

      <p class="font-normal text-white text-sm">
        <b>Profesions: </b>
        <br />
        {{ personaje.occupation[0] }}
        <br />
        {{ personaje.occupation[1] }}
      </p>
      <div class="mt-2">
        <p class="text-white text-sm">
          <b>Cumpleaños:</b>
          <br />
          {{ personaje.birthday }}
        </p>
      </div>
      <div class="items-center">
        <button
          class="text-white rounded bg-gray-500 py-2 px-4 mt-20 border border-orange-700 hover:bg-slate-400"
          @click="enviarFav"
        >
          ❤️
        </button>
      </div>
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
