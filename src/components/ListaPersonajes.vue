<template>
  <div id="container" style="text-align: center">
    <input type="text" v-model="filtro" placeholder="Busca un personaje" />
    <ul
      style="list-style-type: none"
      v-for="(e, index) in filteredCharacters"
      :key="index"
    >
      <li>
        <Personaje :personaje="e" @enviarFavorito="aniadirFavorito" />
      </li>
    </ul>
    <div style="position: absolute; top: 0%">
      <ListaFavs :listaFavs="listaFav" style="margin-top: 0%" />
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
      this.listaFav.push(data);
      console.log(this.listaFav);
    },
  },
};
</script>

<style scoped></style>
