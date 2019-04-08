<template>
   <li>{{jogador.nome}} - {{ jogador.jogadas }} jogadas</li>
</template>

<script>
export default {
  props: {
    jogador: {
      type: Object
    }
  }
};
</script>

<style>
li {
  margin-bottom: 10px;
  letter-spacing: 0.1em;
}
</style>

