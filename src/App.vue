<template>
  <body class="bg-gray-800 w-100">
    <div class="cuerpo">
      <ListaPersonajes :lista="characters" />
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
    return { characters: [] };
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
  },

  mounted() {
    this.loadCharacters();
  },
};
</script>

<style scoped></style>
