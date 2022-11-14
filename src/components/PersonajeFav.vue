<template>
  <div class="items-center text-center flex flex-col ">
    <div class="">
        <img class="rounded-full max-h-32" :src="favorito.img" alt="" />
    </div>
      <h1 class="text-white p-3">{{ favorito.name }}</h1>
    <div class="flex flex-col ">
      <button class="mr-5 rounded-lg text-white bg-orange-700 p-2 min-w-40 mb-2">
       Ver más
      </button>
      <button
      class="rounded-lg text-white bg-red-800 p-2 mb-2 w-20" 
      @click="eliminarFav"
      >
      🗑️
      </button>
    </div>
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
