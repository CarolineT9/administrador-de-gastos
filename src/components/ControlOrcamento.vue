<script setup>
import imagem from '../assets/img/grafico.jpg'
import { formatarMoeda } from '../helpers'

const props = defineProps({
    orcamento: {
        type: Number,
        required: true 
    },
    disponivel: {
        type: Number,
        required: true 
    },
    gastado: {
        type: Number,
        required: true 
    }
})
</script>

<template>
  <div class="duas-colunas">
    <div class="conteudo-grafico">
        <img :src="imagem" alt="Gráfico de Orçamento" />
    </div>
    <div class="conteudo-orcamento">
        <button class="reset-app">Resetar App</button>
        <p>
            <span>Orçamento:  </span>{{ formatarMoeda(orcamento)  }}
        </p>
        <p>
            <span>Disponível:  </span>{{ formatarMoeda(disponivel)  }}
        </p>
        <p>
            <span>Gastos: {{ formatarMoeda(gastado)  }}   </span>
        </p>
    </div>
  </div>
</template>


<style  scoped>
.duas-colunas{
    display: flex;
    flex-direction: column;
}
.duas-colunas > :first-child{
   margin-bottom: 3rem;
}
@media(min-width: 768px){
    .duas-colunas{
        display: flex;
        flex-direction: row;
        gap: 4rem;
        align-items: center;
    }
    .duas-colunas > :first-child{
        margin-bottom: 2rem;
     }
     
}

.reset-app{
    background-color: #db2777;
    border: none;
    width: 100%;
    padding: 1rem;
    cursor: pointer;
    color: var(--branco);
    font-weight: 800;
    text-transform: uppercase;
    border-radius: 1rem;
    transition-property: background-color;
    transition-duration: 300ms;
}
.reset-app:hover{
    background-color: #c41362;
}
.conteudo-orcamento{
       width: 100%; 
}
.conteudo-orcamento p{
    font-size: 2.4rem;
    text-align: center;
    color: var(--cinza-escuro)
}
.conteudo-orcamento span{
    font-weight: 900;
    color: var(--azul);
}

@media(min-width: 768px){
    .conteudo-orcamento p{
        font-size: 2.4rem;
        text-align: left;
    }
 
}
</style>

