<template>
  <div class="text-center ml-20">
    <input type="text" v-model="filtro" placeholder="Busca un personaje" />
  </div>
  <div class="bg-gray-800 mt-6 mb-10">
    <ul v-for="(personaje, index) in filteredCharacters" :key="index" class="">
      <li class="mb-5 max-w-2xl">
        <Personaje
          :personaje="personaje"
          @enviarFav="aniadirElementoFavorito"
        />
      </li>
    </ul>
  </div>
</template>

<script>
import Personaje from "@/components/Personaje.vue";
export default {
  name: "ListaPersonajes",
  emits: ["enviarFav"],
  components: {
    Personaje,
  },
  data() {
    return {
      filtro: "",
    };
  },
  props: {
    lista: {
      type: Array,
    },
  },

  computed: {
    filteredCharacters() {
      return this.lista.filter((character) =>
        character.name.toUpperCase().includes(this.filtro.toUpperCase())
      );
      //.sort((a, b) => a.name.localeCompare(b.name));
    },
  },
  methods: {
    aniadirElementoFavorito(data) {
      this.$emit("enviarFav", data);
      console.log("recibiendo en segundo nivel...");
    },
  },
};
</script>

<style scoped></style>
