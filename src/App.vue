<template>
  <body>
    <div class="cuerpo">
      <ListaPersonajes :lista="characters" />
    </div>
  </body>
</template>

<script>
import axios from "axios";
import ListaPersonajes from "@/components/ListaPersonajes.vue";
export default {
  name: "App",
  components: {
    ListaPersonajes,
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

<style scoped>
.cuerpo {
  background-color: rgb(31, 143, 23);
  min-width: 100%;
  margin: 0;
}
</style>
