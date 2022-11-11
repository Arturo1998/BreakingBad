<template>
  <div class="items-center">
    <div class="">
      <img class="h-50 rounded" :src="favorito.img" alt="" />
    </div>

    <h1 class="text-white p-3">{{ favorito.name }}</h1>

    <button class="rounded-lg text-white bg-orange-700 p-3 ml-10 w-40">
      Ver más
    </button>
    <button
      class="rounded-lg text-white bg-red-800 p-3 ml-10"
      @click="eliminarFav"
    >
      🗑️
    </button>
  </div>
</template>

<script>
export default {
  name: "PersonajeFav",
  components: {},
  data() {
    return {};
  },
  props: {
    favorito: {
      type: Object,
    },
  },
  emits: ["eliminarFav"],
  methods: {
    eliminarFav() {
      if (confirm(`¿Estás seguro de eliminar a ${this.favorito.name}?`))
        this.$emit("eliminarFav", this.favorito);
    },
  },
};
</script>

<style scoped></style>
