<script setup>
import { reactive } from 'vue';

const nome = "guilherme";
const meuObj = {
  nome: "guilherme",
  filmeFavorito: "Rocky",
};

function dizOla(nome) {
  return `${nome} diz: não vou pro curintia`;
}

const enderecoImagemGabi =
  "https://s2-oglobo.glbimg.com/I9Nk6Gwl7alEu4PsBz1ipIohfMo=/0x0:1280x853/924x0/smart/filters:strip_icc()/i.s3.glbimg.com/v1/AUTH_da025474c0c44edd99332dddb09cabe8/internal_photos/bs/2022/7/2/GR3utuSZAbzh6AiJ5gjA/4.png";

const imagemMelo =
  "https://i.ytimg.com/vi/k5fd5SqEZ70/hq720.jpg?sqp=-oaymwEhCK4FEIIDSFryq4qpAxMIARUAAAAAGAElAADIQj0AgKJD&rs=AOn4CLAYlsxi6mcaDphyh2Wzq3ikifd2HA";

const botaoEstaDesabilitado = false;

const gostaDoGabi = false;
const gostaDoMelo = true;

const estaAutorizado = true;

// let contador = 0
const estado = reactive({
  contador: 0,
})

function incrementar() {
  estado.contador++;
}

function decrementar() {
  estado.contador--;
}

</script>

<template>
  <h1>{{ dizOla("gabigol") }}</h1>
  <img v-if="gostaDoGabi" :src="enderecoImagemGabi" alt="" />
  <img v-else-if="gostaDoMelo" :src="imagemMelo" alt="" />
  <h2 v-else>YURI ALBERTOkkkkkkkkkk</h2>

  <h1 v-if="estaAutorizado">Quer um nove bolado?</h1>
  <h1 v-else>Faraó do egito</h1>

  <button :disabled="!botaoEstaDesabilitado">enviar mensagem</button>

  <br>
  <hr>

  {{estado.contador}}

  <button @click="incrementar"  type="button">+</button>
  <button @click="decrementar"  type="button">-</button>
</template>



<style scoped>
img {
  max-width: 300px;
}
</style>
