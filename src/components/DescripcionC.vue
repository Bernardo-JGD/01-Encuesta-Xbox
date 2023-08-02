<template>

<h5 v-if="descripcionHabilitado" >
    {{ descripciones[descripcionPosicion] }}
</h5>

</template>


<script>

export default{
    data: () => ({
        descripciones: [
            "Se perderá todo el progreso no guardado",
            "Selecciona todas las opciones que correspondan",
            "Tus comentarios nos ayudan a mejorar la aplicacion"
        ]
    }),
    props: ["descripcionPosicion", "descripcionHabilitado"],
    methods: {

    }

}

</script>

<style scoped >

h5{
    text-align: center;
    font-size: medium;
}

</style>