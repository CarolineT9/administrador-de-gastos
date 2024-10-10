<script setup>
import {ref} from 'vue'
import fecharModal from '../assets/img/cerrar.svg'
import Alerta from './Alerta.vue';

const error = ref('')

//emit - evento de fechar o modal e de fazer update nos dados
const emit = defineEmits(['fechar-modal', 'update:nome', 'update:quantidade', 'update:categoria'])
const props = defineProps({
  modal:{
    type: Object,
    required: true
  },
  nome:{
    type: String,
    required: true
  },
  quantidade:{
    type: [String, Number],
    required: true
  },
  categoria:{
    type: String,
    required: true
  }

})
const adicionarGasto = () => {
  const { quantidade, categoria, nome } = props;

  // Validate inputs
  if (!nome.trim() || !quantidade || !categoria) {
    error.value = 'Todos os campos são obrigatórios';
    setTimeout(() => { error.value = ''; }, 3000);
    return;
  }

  if (quantidade <= 0) {
    error.value = 'Quantidade não é válida';
    setTimeout(() => { error.value = ''; }, 3000);
    return;
  }


};
</script>

<template>
  <div class="modal">
    <div class="fechar-modal">
      <img @click="$event => $emit('fechar-modal')" :src="fecharModal" alt="">
    </div>
    <div class="conteudo conteudo-formulario"
    :class="[modal.animar ? 'animar' : 'fechar' ]"   
    >
      <form class="novo-gasto"
      @submit.prevent="adicionarGasto"
      
      >
        <legend>Adicionar gasto</legend>
        <Alerta v-if="error">
          {{ error }}
        </Alerta>
        <div class="campo">
          <label for="nome">Gasto: </label>
          <input type="text" id="nome"
          placeholder="Adicionar gasto" 
          :value="nome" 
          @input="$event => $emit('update: nome', $event.target.value)"
          >
        </div>
        <div class="campo">
          <label for="quantidade">Quantidade: </label>
          <input @input="$event => $emit('update:quantidade', $event.target.value)" type="number" id="quantidade"  placeholder="Adicionar quantidade ex: 300" :value="quantidade" >
        </div>
        <div class="campo">
          <label for="categoria">Categoria: </label>
          <select @input="$event => $emit('update:categoria', $event.target.value)"  :value="categoria">
            <option value="">Selecione</option>
            <option value="poupanca">Poupança</option>
            <option value="comida">Comida</option>
            <option value="casa">Casa</option>
            <option value="varios">Vários</option>
            <option value="saude">Saúde</option>
          </select>
        </div>
        <input type="submit" value="Adicionar gastos"/>
      </form>
    </div>
  </div>
</template>



<style>
.modal{
  position: absolute;
  background-color: rgb(0 0 0/ 0.9);
  top: 0;
  right: 0;
  left: 0;
  bottom: 0;
}
.fechar-modal{
  position: absolute;
  top: 3rem;
  right: 3rem;
}
.fechar-modal img{
  width: 3rem;
  cursor: pointer;
}
.conteudo-formulario{
  transition-property: all;
  transition-duration: 300ms;
  transition-timing-function: ease-in;
  opacity: 0;
}
.conteudo-formulario.animar{
  opacity: 1;
}
.conteudo-formulario.fechar{
  opacity: 0;
}
.novo-gasto{
  margin: 10rem auto 0 auto;
  display: grid;
  gap: 2rem;
}

.novo-gasto input[type="submit"]{
  background-color: var(--azul);
  color: var(--branco);
  font-weight: 700;
  cursor: pointer;
}
.novo-gasto label{
  color: var(--branco);
  font-size: 3rem;
}
.novo-gasto legend{
 text-align: center;
 color: var(--branco);
 font-weight: 700;
}
.novo-gasto select, input{
  background-color: var(--cinza-claro);
  border-radius: 1rem;
  padding: 1rem;
  border: none;
  font-size: 2.2rem;
}
.campo{
  display: grid;
  gap: 2rem;
}
</style>