<template>
  <div id="container" style="text-align: right; margin-top: 0">
    <ul
      style="list-style-type: none"
      v-for="(e, index) in listaFavs"
      :key="index"
    >
      <li>
        {{ e.name }}
        <button>Ver más</button>
      </li>
    </ul>
  </div>
</template>

<script>
import Personaje from "@/components/Personaje.vue";
export default {
  name: "ListaFavs",
  components: {
    Personaje,
  },
  data() {
    return {};
  },
  props: {
    listaFavs: {
      type: Array,
    },
  },
};
</script>

<style scoped></style>
