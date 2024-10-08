<script setup>
import Orcamento from './components/Orcamento.vue';
import { ref, reactive} from 'vue';
import ControlOrcamento from './components/ControlOrcamento.vue';
import iconeNovoGasto from './assets/img/nuevo-gasto.svg'
import Modal from  './components/Modal.vue'
const modal = reactive({
  mostrar: false,
  animar: false
})
const orcamento = ref(0)
const disponivel = ref(0)
const definirOrcamento = (valor)=>{
  orcamento.value = ref(valor)
  disponivel.value =  ref(valor)
} 

const mostrarModal = () => {
  modal.mostrar = true
  modal.animar = true
  
}
const fecharModal = () => {
  modal.mostrar = false
  modal.animar = false
  
}
</script>

<template>
  <div>
    <header>
      <h1>Gestor de despesas</h1>
      <div class="conteudo-header conteudo sombra">
        <Orcamento v-if="orcamento === 0 " @definir-orcamento="definirOrcamento"/>
        <ControlOrcamento v-else :orcamento="orcamento" :disponivel="disponivel"/>
      </div>      
    </header>
    <main  v-if="orcamento.value>0">
      <div class="criar-gastos" >
        <img @click="mostrarModal" :src="iconeNovoGasto" alt="icone de novo gasto">
      </div>
    </main>
    <Modal @fechar-modal="fecharModal" v-if="modal.mostrar === true"/>
  </div>
</template>

<style>
:root {
  --azul: #3b82f6;
  --branco: #fff;
  --cinza-claro: #f5f5f5;
  --cinza: #94a3b8;
  --cinza-escuro: #64748b;
  --preto: #000;
}

html {
  font-size: 62, 5%;
  box-sizing: border-box;
}

*,
*::before,
*::after {
  box-sizing: inherit;
}

body {
  font-size: 1.6rem;
  font-family: "Lato", sans-serif;
  background-color: var(--cinza-claro);
}

h1 {
  font-size: 4rem;
}

h2 {
  font-size: 3rem;
}

header h1 {
  background-color: var(--azul);
  margin: 0;
  padding: 50px;
  color: var(--branco);
  text-align: center;
}

.conteudo {
  width: 90%;
  max-width: 80rem;
  margin: 0 auto
}

.conteudo-header {
margin-top: -7rem;
transform: translateY(5rem);
padding: 5rem;
}

.sombra {
box-shadow: 0px 10px 15px -3px rgba(0,0,0,0.1);
background-color: var(--branco);
border-radius: 1.2rem;
padding: 5rem;
}

.criar-gastos{
position: fixed;
bottom: 5rem;
right: 5rem;
}
.criar-gastos img{
  width: 5rem;
  cursor: pointer;
}
</style>
