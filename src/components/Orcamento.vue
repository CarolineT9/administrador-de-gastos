<script setup>
import { ref, defineEmits } from 'vue';
import Alerta from './Alerta.vue';

const orcamento = ref(0)
const erro = ref('');

const emit = defineEmits (['definir-orcamento'])
//validando valor do orçamento

const definirOrcamento = () => {
    if (orcamento.value <= 0 || orcamento.value === "") {
        erro.value = 'Valor inserido inválido'

        setTimeout(() =>{
            erro.value = ""
        },3000)
        return
        
    }
    emit('definir-orcamento', orcamento.value)
}
</script>

<template>
    <form class="orcamento" @submit.prevent="definirOrcamento">
            <Alerta v-if="erro">  
                {{ erro }}             
            </Alerta>
            <div class="campo">
                <label for="novo-orcamento">Definir orçamento:</label>
                <input v-model.number="orcamento" type="number" id="novo-orcamento" class="novo-orcamento"
                    placeholder="adicionar seu orçamento" />
            </div>
            <input type="submit" value="Definir orçamento">
    </form>
</template>



<style scoped>
.orcamento {
    width: 100%;
}

.campo {
    display: grid;
    gap: 2rem
}

.orcamento input[type="number"] {
    background-color: var(--cinza-claro);
    border-radius: 1rem;
    padding: 1rem;
    border: none;
    font-size: 2.2rem;
    text-align: center;

}

.orcamento input[type="submit"] {
    background-color: var(--azul);

    padding: 1rem;
    border: none;
    font-size: 2rem;
    margin-top: 2rem;
    text-align: center;
    color: var(--branco);
    font-weight: 900;
    width: 100%;

}

.orcamento input[type="submit"]:hover {
    background-color: #1048a4;
    cursor: pointer;
    transition: background-color 300ms ease;

}

.orcamento label {
    font-size: 2.8rem;
    text-align: center;
    color: var(--azul);
}
</style>