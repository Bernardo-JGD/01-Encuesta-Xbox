<template>

<div class="contenedor" v-if="habilitarBotonesExperiencia">
    <div @click="
        $emit('componentesEncuestaIncremento'),
        $emit('cambiarEstadosComponentes', 0), 
        $emit('enviarBoton', true), 
        $emit('cambiarTituloDescripcion', 2, 1, true)
        
         " 
         class="opciones"
    >
        <a>Buena</a>
    </div>
    <div @click="
        $emit('componentesEncuestaIncremento'),
        $emit('cambiarEstadosComponentes', 1),
        $emit('enviarBoton', true), 
        $emit('cambiarTituloDescripcion', 3, 1, true)
        
        "
        class="opciones"
    >
        <a>Mala</a>
    </div>
</div>

<!--Contenedor experiencia buena o mala-->
<div v-if="habilitarComponentesExperiencia" >
    <div v-if="habilitarExperienciaBuena">
        <buena-experiencia 
            @experiencia-btn-enviar="ExperienciaBtnEnviar"
            @cambiar-estados-componentes-en-encuesta="cambiarEstadosComponentesEnEncuesta"
            :habilitarExperienciaBuenaBotones="habilitarExperienciaBuenaBotones"
            :habilitarComponenteRespuestas="habilitarComponenteRespuestas"

        />
    </div>
    <div v-if="habilitarExperienciaMala" >
        <mala-experiencia 
            @btnEnviarHabilitar="ExperienciaBtnEnviar"
            @cambiar-estados-componentes-en-encuesta="cambiarEstadosComponentesEnEncuesta"
            :habilitarExperienciaMalaBotones="habilitarExperienciaMalaBotones"
            :habilitarComponenteRespuestas="habilitarComponenteRespuestas"
        />
    </div>
</div>
    
</template>

<script>

import BuenaExperiencia from './BuenaExperienciaC.vue';
import MalaExperiencia from './MalaExperienciaC.vue';

export default{
    data: () => ({

    }),
    props: [
        "habilitarBotonesExperiencia",
        "habilitarComponentesExperiencia",
        "habilitarExperienciaBuena", 
        "habilitarExperienciaMala",
        "habilitarExperienciaBuenaBotones",
        "habilitarExperienciaMalaBotones",
        "habilitarComponenteRespuestas"
    ],
    components: {
        BuenaExperiencia,
        MalaExperiencia
    },
    methods:{
        ExperienciaBtnEnviar(){
            console.log("Entro");
            this.$emit('enviarBoton', false);
        },
        cambiarEstadosComponentesEnEncuesta(){
            this.$emit("componentesEncuestaIncremento");
            this.$emit("cambiarEstadosComponentes");
            console.log("Respuestas");
        }

    }

}

</script>

<style>

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