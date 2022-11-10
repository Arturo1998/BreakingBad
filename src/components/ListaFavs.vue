<template>
  <ul
    v-for="(personaje, index) in listaFavs"
    :key="index"
    class="bg-gray-700 rounded"
  >
    <li class="p-3">
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
