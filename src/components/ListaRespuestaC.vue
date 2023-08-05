<template>

    <div v-for="(opcion, indice) in listaOpciones[posicionListaOpciones]" :key="indice" >
        <label  >
            <input type="checkbox"  >{{ opcion }} 
        </label>
    </div>
    
    

</template>

<script>

export default{
    data: () => ({
        listaOpciones: {
            juegoBueno: [
                "Buena capacidad de respuesta",
                "Controles",
                "El juego cumple las expectativas",
                "Interfaz de usuario",
                "Un gran juego"
            ],
            streamingBueno: [
                "Comienza rápidamente",
                "Juegar en cualquier lugar",
                "No es necesario actualizar el juego",
                "Facilidad de uso",
                "Calidad del streaming"
            ],
            juegoMalo: [
                "Problemas con el juego",
                "Tiempos de carga",
                "Problemas con multijugador",
                "No disfruté el juego"
            ],
            controlesMalo: [
                "El control no vibra o retumba",
                "Los botones no funcionan",
                "Control desconectado",
                "Problemas del control"
            ]

        }
    }),
    props: ["posicionListaOpciones"],
    methods: {
        
    }
}

</script>