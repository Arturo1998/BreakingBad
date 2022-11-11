<template>
  <div class="flex flex-col md:flex-row  bg-gray-800 w-100 p-10">
    <div class="mr-10 col-span-2">
      <ListaPersonajes :lista="characters" @enviarFav="aniadirFavorito" />
    </div>
    <div
      class="max-h-30 20 border-orange-700 top-0 rounded mt-12 mr-5"
    >
      <ListaFavs :listaFavs="favs" @eliminarFav="eliminarElemento" />
    </div>
  </div>
</template>

<script>
import axios from "axios";
import ListaPersonajes from "@/components/ListaPersonajes.vue";
import ListaFavs from "@/components/ListaFavs.vue";
export default {
  name: "App",
  components: {
    ListaPersonajes,
    ListaFavs,
  },

  data() {
    return { characters: [], favs: [], filtro: "" };
  },
  methods: {
    async loadCharacters() {
      try {
        const response = await axios.get(
          `https://www.breakingbadapi.com/api/characters`
        );
        this.characters = response.data;
      } catch (error) {
        console.log(error);
      }
    },

    aniadirFavorito(data) {
      const result = this.favs.filter(
        (personaje) => personaje.char_id === data.char_id
      );
      if (result.length === 0) {
        this.favs.push(data);
        console.log(this.favs);
      }
    },

    eliminarElemento(data) {
      this.favs = this.favs.filter((el) => el !== data);
    },
  },

  mounted() {
    this.loadCharacters();
  },
};
</script>

<style scoped></style>
