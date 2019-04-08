<template>
   <div>
      <h1>Ranking</h1>
      <ul>
         <jogador v-for="jogador in jogadores" v-bind:key="jogador.id" v-bind:jogador="jogador" ></jogador>
      </ul>
   </div>
</template>

<script>
import jogador from "./jogador.vue";

export default {
  data() {
    return {
      jogadores: [
        {
          id: 1,
          nome: "Renan",
          jogadas: 15
        },
        {
          id: 2,
          nome: "Maria",
          jogadas: 20
        },
        {
          id: 3,
          nome: "Jose",
          jogadas: 25
        }
      ]
    };
  },
  components: {
    jogador
  }
};
</script>

<style scoped>
div {
  align-items: center;
  width: 30%;
}

h1 {
  margin-top: 0;
  text-transform: uppercase;
}
</style>


