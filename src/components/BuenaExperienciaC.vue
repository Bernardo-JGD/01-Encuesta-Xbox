<template>

    <div v-if="!respuestasVisibles" class="contenedor"  >
        <div class="opciones" @click="habilitarRespuestasJuego(), btnEnviarHabilitar()" >
            <a>Juego</a>
        </div>
        <div class="opciones" @click="habilitarRespuestasStreaming(), btnEnviarHabilitar()" >
            <a>Streaming</a>
        </div>
    </div>

    <div v-if="respuestasVisibles" >
        <respuestas :posicion-lista-opciones="posicionListaOpciones" />
    </div>

</template>

<script>

import Respuestas from './ListaRespuestaC.vue';

export default{

    data: () => ({
        respuestasVisibles: false,
        posicionListaOpciones: "juegoBueno",
    }),
    components: {
        Respuestas
    },
    methods: {
        habilitarRespuestasJuego(){
            this.respuestasVisibles = true;
        },
        habilitarRespuestasStreaming(){
            this.respuestasVisibles = true;
            this.posicionListaOpciones = "streamingBueno";
        },
        btnEnviarHabilitar(){
            this.$emit("ExperienciaBtnEnviar")
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