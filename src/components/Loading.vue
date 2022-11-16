<template>
  <div class="flex justify-center items-center mb-6">
    <h1 class="text-2xl mr-6 text-white">Buscando a {{ this.busca }}</h1>
    <div
      class="spinner-border border-orange-500 animate-spin inline-block w-8 h-8 border-4"
      role="status"
    ></div>
  </div>
</template>

<script>
export default {
  name: "Loading",
  props: {
    busca: {
      type: String,
    },
  },
};
</script>

<style scoped></style>
