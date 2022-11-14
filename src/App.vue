<template>
  <Buscador @buscarPersonaje="filtrar" v-model="filtro" />
  <div class="flex flex-col md:flex-row bg-gray-800 w-100 p-10">
    <div class="mr-10 col-span-2">
      <ListaPersonajes
        :lista="filtrarPersonajes"
        @enviarFav="aniadirFavorito"
      />
    </div>
    <div class="max-h-30 20 border-orange-700 top-0 rounded mt-12 mr-5">
      <ListaFavs :listaFavs="favs" @eliminarFav="eliminarElemento" />
    </div>
  </div>
</template>

<script>
import axios from "axios";
import Buscador from "@/components/Buscador.vue";
import ListaPersonajes from "@/components/ListaPersonajes.vue";
import ListaFavs from "@/components/ListaFavs.vue";
export default {
  name: "App",
  components: {
    ListaPersonajes,
    ListaFavs,
    Buscador,
  },

  data() {
    return { characters: [], favs: [], filtrar_por: "", filtro: "" };
  },

  computed: {
    filtrarPersonajes() {
      if(this.filtrar_por!="") {
        return this.characters.filter((character) =>
        character.name.toUpperCase().includes(this.filtrar_por.toUpperCase())
      );
      } else{
        return "";
      }
      
    },
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

    filtrar(data) {
      this.filtrar_por = data;
      console.log(this.filtrar_por);
    },
  },

  mounted() {
    this.loadCharacters();
  },
};
</script>

<style scoped></style>
