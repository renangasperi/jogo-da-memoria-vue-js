<template>
  <div id="app" >
    <tutorial/>
    <listaCartas/>
    <ranking/>
  </div>
</template>

<script>
import listaCartas from "./components/listaCartas";
import ranking from "./components/ranking.vue";
import tutorial from "./components/tutorial.vue";

export default {
  name: "app",
  components: {
    listaCartas,
    ranking,
    tutorial
  }
};
</script>

<style>
body {
  font-family: helvetica;
  background-color: #585454;
  color: white;
}
#app {
  display: flex;
  flex-direction: row;
  text-align: center;
}
</style>
