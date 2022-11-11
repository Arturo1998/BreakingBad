<template>
  <ul v-for="(personaje, index) in listaFavs" :key="index" class="rounded">
    <li class="p-3 hover:bg-gray-900 mb-0.25 border border-orange-700 rounded">
      <PersonajeFav :favorito="personaje" @eliminarFav="borrarFav" />
    </li>
  </ul>
</template>

<script>
import PersonajeFav from "@/components/PersonajeFav.vue";
export default {
  emits: ["eliminarFav"],
  name: "ListaFavs",
  components: {
    PersonajeFav,
  },
  data() {
    return {};
  },
  props: {
    listaFavs: {
      type: Array,
    },
  },
  methods: {
    borrarFav(data) {
      this.$emit("eliminarFav", data);
    },
  },
};
</script>

<style scoped></style>
