<template>

<h3>
    {{ titulos[tituloPosicion] }}
</h3>

</template>

<script>

export default{
    data: () => ({
        titulos: [
            "¿Estás seguro?",
            "¿Cómo es tu experiencia de juego?",
            "¡Excelente! ¿Qué te gustó?",
            "Ayudamos a mejorar",
            "Juego",
            "Streaming",
            "Controles",
            "¿Otra cosa?",
            "¡Gracias!",
            "Cuéntanos más"
        ]
    }),
    props: ["tituloPosicion"],
    methods: {
        
    }
}

</script>

<style scoped >

h3{
    text-align: center;
}

</style>