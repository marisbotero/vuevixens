<template>
  <div id="app">
    <MainTitle/>
    <ListadoFrutas :frutas="frutas"/>
  </div>
</template>

<script>
import MainTitle from "./components/MainTitle";
import ListadoFrutas from "./components/ListadoFrutas";
export default {
  name: "App",
  data() {
    return {
      frutas: [
        { nombre: "Manzana", cantidad: 10 },
        { nombre: "Pera", cantidad: 0 }
      ]
    };
  },
  components: {
    MainTitle,
    ListadoFrutas
  }
};
</script>

<style>
body {
  background-image: url("https://i.pinimg.com/originals/67/aa/47/67aa472ef96fa88171c59eadd34883ab.jpg");
}
</style>
