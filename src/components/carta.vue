<template>
    <label>
      <input v-bind:id="carta.id" class="checkbox" type="checkbox"/>
      <div class="carta">
        <div class="frente" v-on:click="emiteJogadas">?</div>
        <div class="atras">{{ carta.valor }}</div>
      </div>
    </label>
</template>

<script>
export default {
  props: {
    carta: {
      type: Object
    }
  },
  methods: {
    emiteJogadas: function() {
      this.$emit("novaJogada");
    }
  }
};
</script>

<style scoped>
label {
  perspective: 800px;
  transform-style: preserve-3d;
  width: 75px;
  height: 95px;
  cursor: pointer;
}

.carta {
  height: 100%;
  width: 100%;
  transform-style: preserve-3d;
  transition: all 600ms;
}

.carta div {
  font-size: 55px;
  font-weight: bold;
  position: absolute;
  height: 100%;
  width: 100%;
  background: #841414;
  text-align: center;
  line-height: 90px;
  backface-visibility: hidden;
  border-radius: 10px;
}
.carta .atras {
  background: #222;
  transform: rotateX(180deg);
}

label:hover .carta {
  transform: rotateX(20deg);
  box-shadow: 0px 0px 25px -10px rgba(255, 255, 255, 1);
}

input {
  display: none;
}

:checked + .carta {
  transform: rotateX(180deg);
}

label:hover :checked + .carta {
  transform: rotateX(160deg);
  -webkit-transform: rotateX(160deg);
  box-shadow: 0 20px 20px rgba(255, 255, 255, 0.2);
}
</style>
