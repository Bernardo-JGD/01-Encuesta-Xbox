<template>

    <div v-for="(opcion, indice) in listaOpciones[posicionListaOpciones]" :key="indice" >
        <label  >
            <!-- v-model="arregloRespuestas" @value="opcion" @click="metodoPrueba(opcion)" -->
            <input type="checkbox" @click="metodoPrueba(opcion)"  >{{ opcion }} 
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

        },
        arregloRespuestas: []
    }),
    props: ["posicionListaOpciones"],
    mounted(){
        console.log(this.posicionListaOpciones);
        this.listaOpciones[this.posicionListaOpciones].forEach(opcion =>{
            let opcionSinEspacios = opcion.replace(/\s/g, "_");
            this.arregloRespuestas[opcionSinEspacios] = false;
            
        });
    },
    methods: {
        metodoPrueba(opcion){
            /*
            if (this.arregloRespuestas.includes(opcion)) {
                // Si ya existe en el arreglo, lo eliminamos
                const index = this.arregloRespuestas.indexOf(opcion);
                this.arregloRespuestas.splice(index, 1);
            } else {
                // Si no existe en el arreglo, lo agregamos
                this.arregloRespuestas.push(opcion);
            }
             */
             let opcionSinEspacios = opcion.replace(/\s/g, "_");
            console.log(this.arregloRespuestas);
            this.arregloRespuestas[opcionSinEspacios] = !this.arregloRespuestas[opcionSinEspacios];
            /*
            console.log(opcion);
            this.arregloRespuestas.push(opcion);
            console.log(this.arregloRespuestas);
            */
            
        }
    }
}

</script>