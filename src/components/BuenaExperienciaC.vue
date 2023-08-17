<template>
    <!--experiencias buenas-->
    <div v-if="habilitarExperienciaBuenaBotones" class="contenedor"  >
        <div class="opciones" @click="emitHabilitarExperienciaBuenaJuegoRespuestas(), posicionListaOpcionesJuegoBueno()" >
            <a>Juego</a>
        </div>
        <div class="opciones" @click="emitHabilitarExperienciaBuenaJuegoRespuestas(), posicionListaOpcionesJuegoStreaming()" >
            <a>Streaming</a>
        </div>
    </div>
    <!--respuestas-->
    <div v-if="habilitarComponenteRespuestas" >
        <respuestas :posicion-lista-opciones="posicionListaOpciones" />
    </div>

</template>

<script>

import Respuestas from './ListaRespuestaC.vue';

export default{

    data: () => ({
        posicionListaOpciones: "",
    }),
    props: [
        "habilitarExperienciaBuenaBotones", 
        "habilitarComponenteRespuestas"
    ],
    components: {
        Respuestas
    },
    methods: {
        emitHabilitarExperienciaBuenaJuegoRespuestas(){
            this.$emit("cambiarEstadosComponentesEnEncuesta");
        },
        emitHabilitarExperienciaBuenaStreamingRespuestas(){
            this.$emit("cambiarEstadosComponentesEnEncuesta");
        },
        btnEnviarHabilitar(){
            this.$emit("ExperienciaBtnEnviar")
        },
        posicionListaOpcionesJuegoBueno(){
            this.posicionListaOpciones = "juegoBueno";
        },
        posicionListaOpcionesJuegoStreaming(){
            this.posicionListaOpciones = "streamingBueno";
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