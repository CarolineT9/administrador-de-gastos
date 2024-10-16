<script setup>
import { formatarMoeda } from '../helpers/index'
import { formatarData } from '../helpers/index'

import IconoAhorro from '../assets/img/icono_ahorro.svg'
import IconoCasa from '../assets/img/icono_casa.svg'
import IconoComida from '../assets/img/icono_comida.svg'
import IconoGastos from '../assets/img/icono_gastos.svg'
import IconoOcio from '../assets/img/icono_ocio.svg'
import IconoSalud from '../assets/img/icono_salud.svg'
import IconoSuscripciones from '../assets/img/icono_suscripciones.svg'

//dicionario de icones

const diccionarioIconos = {
        investimento : IconoAhorro,
        comida : IconoComida,
        casa : IconoCasa,
        gastos : IconoGastos,
        lazer : IconoOcio,
        saude : IconoSalud,
        varios : IconoSuscripciones
    }

const props = defineProps({
    gasto: {
        type: Object,
        required: true
    }
})
</script>

<template>
    <div class="gasto sombra">
        <div class="container">
            <img :src="diccionarioIconos[gasto.categoria]" alt="icone gastos" class="icone">
            <div class="detalhes">
                
                <p class="categoria">{{ gasto.categoria }}</p>
                <p class="nome">{{ gasto.nome }}</p>
                <p  class="data">
                    Data:
                    <span>
                        {{ formatarData(gasto.data) }}
                    </span>
                    
                </p>
                <p class="quantidade">{{ formatarMoeda(gasto.quantidade) }}</p>
            </div>
        </div>
       
    </div>
</template>


<style>
.gasto{
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin-bottom: 2rem;
}
.container{
    display: flex;
    align-items: center;
    gap:  2rem
}
.icone{
    width: 5rem;
}
.detalhes p{
    margin: 0 0 1rem 0;
}

.categoria{
    color: var(--cinza);
    font-size: 1.2rem;
    text-transform: uppercase;
    font-weight: 900;
}
.nome{
    color: var(--cinza-escuro);
    font-size: 2.4rem;
    font-weight: 700;
    cursor: pointer;
}

.data{
    color: var(--cinza-escuro);
    font-size: 1.6rem;
    font-weight: 900;
}
.data span{

    font-weight: 400;
}
.quantidade{
    font-size: 3rem;
    font-weight: 900;
    margin: 0;
}
</style>