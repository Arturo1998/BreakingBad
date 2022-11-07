<template>
  <div id="container" class="divBox flex items-center justify-center">
    <p>{{ personaje.name }}</p>
    <button @click="enviarFav">❤️</button>
    <img :src="personaje.img" alt="" style="max-width: 200px" />
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
