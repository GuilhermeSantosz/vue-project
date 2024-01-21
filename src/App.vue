<script setup>
import { reactive } from 'vue';

const nome = "guilherme";
const meuObj = {
  nome: "guilherme",
  filmeFavorito: "Rocky",
};

function dizOla() {
  return "UP the Irons";
}

const imagemSteve =
"https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcTYF0zwdx2FqYIQgkJebwpFjmgcDnZVSftqfsyT5_-IFA&s";

const imagemBruce =
  "https://s2-g1.glbimg.com/_2yHi4edVB_we_QTDhaTaY2w_-E=/0x0:1700x1065/984x0/smart/filters:strip_icc()/i.s3.glbimg.com/v1/AUTH_59edd422c0c84a879bd37670ae4f538a/internal_photos/bs/2022/T/B/uVGugSSFirAUUDgxGV5g/dsc-0555.jpg";

const botaoEstaDesabilitado = false;

const gostaDoSteve = true;
const gostaDoBruce = true;

const estaAutorizado = true;

// let contador = 0
const estado = reactive({
  contador: 0,
  email: '',
  saldo: 5000,
  transferindo: 0,
})

function incrementar() {
  estado.contador++;
}

function decrementar() {
  estado.contador--;
}

function alteraEmail(evento) {
  estado.email = evento.target.value;
}

function mostraSaldoFuturo() {
  const {saldo, transferindo } = estado;
  return saldo - transferindo;
}

function validadoValorTransferencia() {
  const {saldo, transferindo } = estado;
  return saldo >= transferindo;
}

</script>

<template>
  <h1>{{ dizOla() }}</h1>
  <img v-if="gostaDoSteve" :src="imagemSteve" alt="" />
  <img v-else-if="gostaDoBruce" :src="imagemBruce" alt="" />
  <h2 v-else>Não gosta da banda :(</h2>

  <h1 v-if="estaAutorizado">Steve Harris</h1>
  <h1 v-else>Bruce Dickinson</h1>

  <button :disabled="!botaoEstaDesabilitado">enviar mensagem</button>

  <br>
  <hr>

  {{estado.contador}}

  <button @click="incrementar"  type="button">+</button>
  <button @click="decrementar"  type="button">-</button>


  <br>
  <hr>
 
  {{ estado.email}}
  <input type="email" @keyup="alteraEmail">

  <br>
  <hr>
 
  Saldo: {{ estado.saldo }} <br>
  Transferindo:{{ estado.transferindo }} <br>
  Saldo depois da tranferência: {{ mostraSaldoFuturo() }} <br>
  <input class="campo"  :class="{invalido: !validadoValorTransferencia()}"  @keyup="evento => estado.transferindo = evento.target.value"  type="number" placeholder="Quantia para transferir">
  <button v-if="validadoValorTransferencia()">Tranferir</button>
  <span v-else>Valor maior que o saldo</span>

</template>



<style scoped>
img {
  max-width: 300px;
}

.invalido {
  outline-color: red;
  border-color: red;
}

.campo {
  border: 2px solid blue;
}
</style>
