<template>
   <div class="container">
      <h1>JOGO DA MEMORIA</h1>
      <div class="dados_jogador">
         <label for="jogador"></label>
         <input name="jogador" placeholder="Nome do jogador" v-model="nomeJogador">
         <button v-on:click="embaralhar">Novo jogo</button>
      </div>
      <div class="container2">
         <carta v-for="carta in cartas" v-bind:key="carta.id" v-bind:carta="carta" v-on:novaJogada="Jogada(carta)"></carta>
      </div>
      <span>Contador de jogadas: {{ jogadas }}</span>
   </div>
</template>
<script>
import carta from "./carta.vue";
import dados from "../services/dados.js";

export default {
  data() {
    return {
      cartas: dados,
      jogadas: 0,
      guardaValor: 0,
      guardaId: 0,
      paresEncontrados: 0,
      nomeJogador: ""
    };
  },
  components: {
    carta
  },
  methods: {
    embaralhar: function() {
      this.cartas.sort(() => Math.random() - 0.5);
      this.jogadas = 0;
      this.guardaValor = 0;
      this.guardaId = 0;
      this.paresEncontrados = 0;
      this.cartas.map(carta => {
        document.getElementById(carta.id).checked = false;
      });
    },
    Jogada: function(carta) {
      if (this.guardaValor == 0) {
        this.guardaValor = carta.valor;
        this.guardaId = carta.id;
      } else {
        if (this.guardaValor === carta.valor) {
          this.paresEncontrados++;

          if (this.paresEncontrados === 10) {
            setTimeout(() => {
              alert(
                "PARABÉNS!!!! VOCÊ COMPLETOU O JOGO EM " +
                  this.jogadas +
                  " JOGADAS!! APERTE OK PARA COMEÇAR UM NOVO JOGO"
              );
              this.embaralhar();
            }, 700);
          }
        } else {
          setTimeout(() => {
            document.getElementById(this.guardaId).checked = false;
            document.getElementById(carta.id).checked = false;
            this.guardaId = 0;
          }, 1300);
        }
        this.guardaValor = 0;
        this.jogadas++;
      }
    }
  }
};
</script>

<style scoped>
.container {
  width: 40%;
  display: flex;
  justify-content: center;
  align-items: center;
  flex-wrap: wrap;
  flex-direction: column;
}

.container2 {
  padding: 0 20px;
  height: 420px;
  display: flex;
  justify-content: space-between;
  flex-wrap: wrap;
}

h1 {
  text-transform: uppercase;
  margin: 0;
}

button {
  margin: 10px;
  border-radius: 5px;
  font-weight: bold;
  background: #841414;
  color: white;
  padding: 5px 50px;
  border: 0;
  box-shadow: 1px 1px 4px 0px rgba(0, 0, 0, 0.75);
}

button:hover {
  background: #9e1b1b;
  cursor: pointer;
}

span {
  font-size: 20px;
}

input {
  padding: 3px 10px;
  width: 200px;
  box-shadow: 1px 1px 4px 0px rgba(0, 0, 0, 0.75);
}
</style>
