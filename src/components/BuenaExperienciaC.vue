<template>

    <div v-if="!respuestasVisibles" class="contenedor"  >
        <div class="opciones" @click="habilitarRespuestas" >
            <a>Juego</a>
        </div>
        <div class="opciones" >
            <a>Streaming</a>
        </div>
    </div>

    <div v-if="respuestasVisibles" >
        <respuestas />
    </div>

</template>

<script>

import Respuestas from './ListaRespuestaC.vue';

export default{

    data: () => ({
        respuestasVisibles: false,
    }),
    components: {
        Respuestas
    },
    methods: {
        habilitarRespuestas(){
            this.respuestasVisibles = true;
        }
    }

}

</script>


<style scoped >

.contenedor{
    width: 400px;
    display: flex;
    justify-content: space-around;
}

.opciones{
    padding: 40px;
    background: #2d3036;
    border-radius: 8px;
    width: 3rem;
    display: flex;
    justify-content: center;
}

.opciones:hover{
    background: #515863;
    cursor: pointer;
}

</style>