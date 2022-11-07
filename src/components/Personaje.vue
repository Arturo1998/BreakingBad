<template>
  <div id="container" style="text-align: center">
    {{ personaje.name }} <br />
    <img :src="personaje.img" alt="" style="max-width: 200px" /> <br />
    <button @click="enviarFav">❤️</button>
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
