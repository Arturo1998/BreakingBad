<template>
  <body class="bg-gray-800 w-100">
    <ListaPersonajes :lista="characters" @agregarFav="aniadirFavorito" />
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
    return { characters: [], favs: [] };
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
      }
    },
  },

  mounted() {
    this.loadCharacters();
  },
};
</script>

<style scoped></style>
