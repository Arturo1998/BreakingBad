<template>
  <div
    class="m-auto bg-gradient-to-b from-gray-900 via-gray-800 to-amber-900 min-h-screen"
  >
    <img
      src="./assets/imagenFondo.jpg"
      alt=""
      class="min-w-100 max-h-96 mx-auto"
    />
    <div class="mt-8 mb-5 flex justify-center">
      <Buscador @buscarPersonaje="loadCharacters" v-model="filtro" />
    </div>
    <div v-if="isLoading">
      <Loading :busca="inputUsuario" />
    </div>

    <div class="text-center flex flex-col md:flex-row w-100">
      <div class="m-auto">
        <h1
          class="mb-2 rounded-lg bg-gray-600 text-white border border-orange-700 p-2"
          v-if="characters.length != 0"
        >
          Tu búsqueda
        </h1>
        <h1
          class="mb-2 mt-0 rounded-lg text-gray-400 p-2 text-xl"
          v-else-if="!isLoading"
        >
          Introduce un nombre para ver los personajes
        </h1>

        <ListaPersonajes
          :lista="characters"
          @enviarFav="aniadirFavorito"
          bg-gray-80
        />
      </div>
      <div
        class="border-orange-700 rounded p-50 text-center m-auto mt-1 mb-10"
        v-if="this.favs.length > 0"
      >
        <h1
          class="mb-5 rounded-lg bg-gray-600 text-white border border-orange-700 p-2"
        >
          Lista de favoritos
        </h1>
        <ListaFavs :listaFavs="favs" @eliminarFav="eliminarElemento" />
      </div>
    </div>
  </div>
</template>

<script>
/*<button @click="" class="rounded-lg text-white bg-orange-700 p-2 w-auto mb-2">
        Cargar Personajes
      </button>*/
import Loading from "@/components/Loading.vue";
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
    Loading,
  },
  data() {
    return {
      characters: [],
      favs: [],
      inputUsuario: "",
      filtro: "",
      isLoading: false,
    };
  },
  mounted() {
    if (localStorage.getItem("favs")) {
      this.favs = JSON.parse(localStorage.getItem("favs"));
    }
  },
  methods: {
    async loadCharacters(data) {
      this.inputUsuario = data;
      this.isLoading = true;
      try {
        const response = await axios.get(
          `https://www.breakingbadapi.com/api/characters?name=${this.inputUsuario}`
        );
        setTimeout(() => {
          this.isLoading = false;
          this.characters = response.data;
        }, 1500);
      } catch (error) {
        console.log(error);
      }
    },
    aniadirFavorito(data) {
      if (!this.favs.includes(data)) {
        this.favs.push(data);
        this.guardarLocal();
      } else {
        return null;
      }
    },
    eliminarElemento(data) {
      this.favs = this.favs.filter((el) => el !== data);
      localStorage.setItem("favs", JSON.stringify(this.favs));
    },

    guardarLocal() {
      const parsed = JSON.stringify(this.favs);
      localStorage.setItem("favs", parsed);
    },
  },
};
</script>

<style scoped></style>
