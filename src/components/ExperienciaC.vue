<template>

<div class="contenedor" v-if="!experiencia">
    <div @click="habilitarExperienciaBuena(), $emit('regresarBoton'), $emit('enviarBoton'), $emit('cambiarTituloDescripcion', 2, 1)"  class="opciones">
        <a>Buena</a>
    </div>
    <div @click="habilitarExperienciaMala(), $emit('regresarBoton'), $emit('enviarBoton'), $emit('cambiarTituloDescripcion', 3, 1)" class="opciones" >
        <a>Mala</a>
    </div>
</div>

<!--Contenedor experiencia buena o mala-->
<div v-if="experiencia" >
    <div v-if="experienciaB">
        <buena-experiencia />
    </div>
    <div v-if="experienciaM" >
        <mala-experiencia />
    </div>
</div>
    
</template>

<script>

import BuenaExperiencia from './BuenaExperienciaC.vue';
import MalaExperiencia from './MalaExperienciaC.vue';

export default{
    data: () => ({
        experiencia: false,
        experienciaB: false,
        experienciaM: false,
    }),
    components: {
        BuenaExperiencia,
        MalaExperiencia
    },
    methods:{
        habilitarExperienciaBuena(){
            this.experiencia = true;
            this.experienciaB = true;
        },
        habilitarExperienciaMala(){
            this.experiencia = true;
            this.experienciaM = true;
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