<script setup>
import fecharModal from '../assets/img/cerrar.svg'

const emit = defineEmits(['fechar-modal'])
</script>

<template>
  <div class="modal">
    <div class="fechar-modal">
      <img @click="$event => $emit('fechar-modal')" :src="fecharModal" alt="">
    </div>
    <div class="conteudo">
      <form >
        <legend>Adicionar gasto</legend>
        <div class="campo">
          <label for="nome">Gasto: </label>
          <input type="text" id="nome" placeholder="Adicionar gasto" >
        </div>
        <div class="campo">
          <label for="quantidade">Quantidade: </label>
          <input type="number" id="quantidade"  placeholder="Adicionar quantidade ex: 300" >
        </div>
        <div class="campo">
          <label for="categoria">Categoria: </label>
          <select value="poupança" >
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
</style>