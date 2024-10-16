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
        ahorro : IconoAhorro,
        comida : IconoComida,
        casa : IconoCasa,
        gastos : IconoGastos,
        ocio : IconoOcio,
        salud : IconoSalud,
        suscripciones : IconoSuscripciones
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
        <div class="conteudo">
            <div class="detalhes">
                <img :src="diccionarioIconos[gasto.categoria]" alt="icone gastos" class="icone">
                <p>{{ gasto.categoria }}</p>
                <p class="nome">{{ gasto.nome }}</p>
                <p>{{ formatarData(gasto.data) }}</p>

            </div>
        </div>
        <p>{{ formatarMoeda(gasto.quantidade) }}</p>
    </div>
</template>


<style></style>