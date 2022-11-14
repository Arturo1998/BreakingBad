<template>
    <div class="text-center bg-gray-800">
        <input type="text" v-model="filtro" placeholder="Busca un personaje"
        class="bg-transparent border text-white mr-1 py-1 px-2 " />
        <button @click="buscarPersonaje" class="mr-5 rounded-lg text-white bg-orange-700 mt-2 p-2 min-w-40 mb-2 hover:bg-orange-800">Buscar</button>
       
    </div>
  </template>
  
  <script>
 
  export default {
    name: "Buscador",
    emits: ["buscarPersonaje"],
    components: {
     
    },
    data() {
      return {
        filtro: "",
      };
    },
  
    methods: {
        buscarPersonaje(){
            this.$emit("buscarPersonaje", this.filtro);
        },
    },
  };
  </script>
  
  <style scoped></style>
  