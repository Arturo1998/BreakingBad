<template>
  <ul
    v-for="(e, index) in listaFavs"
    :key="index"
    class="hover:bg-emerald-900 max-w-md divide-y divide-gray-200 dark:divide-gray-700 bg-green-900"
  >
    <li class="pb-3 sm:pb-4">
      <div class="flex items-center space-x-4">
        <div class="p-5 flex-shrink-0">
          <img class="w-12 h-12 rounded-full" :src="e.img" alt="" />
        </div>
        <div
          class="inline-flex items-center text-base font-semibold text-gray-900 dark:text-white px-5"
        >
          {{ e.name }}
        </div>
        <div
          class="inline-flex items-center text-base font-semibold text-gray-900 dark:text-white px-5"
        >
          <button>Ver más</button>
        </div>
      </div>
    </li>
  </ul>
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
