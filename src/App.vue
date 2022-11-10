<template>
  <body class="bg-gray-800 w-100">
    <div class="grid grid-cols-2">
      <div class="ml-10">
        <ListaPersonajes :lista="characters" @enviarFav="aniadirFavorito" />
      </div>
      <div class="max-w-lg border border-orange-700 rounded ml-10 mt-6">
        <ListaFavs :listaFavs="favs" @eliminarFav="eliminarElemento" />
      </div>
    </div>
  </body>
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
