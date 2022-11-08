<template>
  <div
    class="m-5 p-5 flex items-center rounded-lg border max-w-xl hover:bg-gray-100 border-orange-700 bg-gray-700 hover:bg-gray-900"
  >
    <img class="w-64" :src="personaje.img" alt="" />
    <div class="flex-col p-4">
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
        @click="enviarFav()"
      >
        ❤️
      </button>
    </div>
  </div>
</template>

<script>
export default {
  name: "ListaPersonajes",
  emits: ["enviarFavorito"],
  data() {
    return {};
  },
  props: {
    personaje: {
      type: Object,
    },
  },
  methods: {
    enviarFav() {
      this.$emit("enviarFavorito", this.personaje);
    },
  },
};
</script>

<style scoped></style>
