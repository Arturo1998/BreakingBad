<template>
  <div class="text-center">
    <input type="text" v-model="filtro" placeholder="Busca un personaje" />
  </div>
  <div>
    <div class="grid grid-cols-3 bg-gray-800">
      <ul v-for="(e, index) in filteredCharacters" :key="index" class="">
        <li class="">
          <Personaje :personaje="e" @enviarFavorito="aniadirFavorito" />
        </li>
      </ul>
      <div class="flex-auto max-w-lg border border-orange-700 rounded">
        <ListaFavs :listaFavs="listaFav" />
      </div>
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
  emits: ["agregarFav"],

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
        this.listaFav.push(data);
      }
    },
  },
};
</script>

<style scoped></style>
