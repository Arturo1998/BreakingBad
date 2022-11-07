<template>
  <div id="container">
    <div class="text-center">
      <input type="text" v-model="filtro" placeholder="Busca un personaje" />
    </div>
    <ul v-for="(e, index) in filteredCharacters" :key="index">
      <li>
        <Personaje :personaje="e" @enviarFavorito="aniadirFavorito" />
      </li>
    </ul>
    <div style="position: absolute; top: 0%">
      <ListaFavs :listaFavs="listaFav" />
    </div>
  </div>
</template>

<script>
import Personaje from "@/components/Personaje.vue";
import ListaFavs from "@/components/ListaFavs.vue";
export default {
  name: "ListaPersonajes",
  components: {
    Personaje,
    ListaFavs,
  },
  data() {
    return {
      filtro: "",
      listaFav: [],
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
    aniadirFavorito(data) {
      const result = this.listaFav.filter(
        (personaje) => personaje.char_id === data.char_id
      );
      if (result.length === 0) {
        console.log(this.listaFav);
        this.listaFav.push(data);
      }
    },
  },
};
</script>

<style scoped></style>
