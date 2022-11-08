<template>
  <ul v-for="(e, index) in listaFavs" :key="index" class="bg-gray-700 rounded">
    <li class="p-3">
      <div class="flex items-center">
        <div class="p-5">
          <img class="w-12 h-16 rounded-full" :src="e.img" alt="" />
        </div>
        <div class="items-center font-semibold text-white px-5">
          {{ e.name }}
        </div>
        <div class="items-center text-white px-5">
          <button class="rounded-lg bg-orange-700 p-3">Ver más</button>
          <button
            class="rounded-lg bg-red-800 p-3 ml-3"
            @click="eliminarPersonaje()"
          >
            🗑️
          </button>
        </div>
      </div>
    </li>
  </ul>
</template>

<script>
import Personaje from "@/components/Personaje.vue";
export default {
  emits: ["eliminarElemento"],
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
