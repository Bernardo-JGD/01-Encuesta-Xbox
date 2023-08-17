<template>

    <div v-if="habilitarExperienciaMalaBotones" class="contenedor" >

        <div class="opciones" @click="emitHabilitarExperienciaMalaJuegoRespuestas(), posicionListaOpcionesJuegoMalo()" >
            <a>Juego</a>
        </div>

        <div class="opciones" @click="emitHabilitarExperienciaMalaControlesRespuestas(), posicionListaOpcionesControlesMalo()" >
            <a>Controles</a>
        </div>

        <div class="opciones" @click="emitHabilitarExperienciaMalaStreamingRespuestas(), posicionListaOpcionesStreamingMalo()" >
            <a>Streaming</a>
        </div>

    </div>

    <!--Respuestas-->
    <div v-if="habilitarComponenteRespuestas" >
        <respuestas :posicion-lista-opciones="posicionListaOpciones" />
    </div>
    
</template>

<script>

import Respuestas from './ListaRespuestaC.vue';

export default{

    data: () => ({
        posicionListaOpciones: ""
    }),
    components: {
        Respuestas
    },
    props: [
        "habilitarExperienciaMalaBotones",
        "habilitarComponenteRespuestas"
    ],
    methods: {
        emitHabilitarExperienciaMalaJuegoRespuestas(){
            this.$emit("cambiarEstadosComponentesEnEncuesta");
        },
        emitHabilitarExperienciaMalaControlesRespuestas(){
            this.$emit("cambiarEstadosComponentesEnEncuesta");
        },
        emitHabilitarExperienciaMalaStreamingRespuestas(){
            this.$emit("cambiarEstadosComponentesEnEncuesta");
        },
        posicionListaOpcionesJuegoMalo(){
            this.posicionListaOpciones = "juegoMalo";
        },
        posicionListaOpcionesControlesMalo(){
            this.posicionListaOpciones = "controlesMalo";
        },
        posicionListaOpcionesStreamingMalo(){
            this.posicionListaOpciones = "StreamingMalo";
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
    margin: 0px 5px 0px 5px;
    width: 3rem;
    display: flex;
    justify-content: center;
}

.opciones:hover{
    background: #515863;
    cursor: pointer;
}

</style>