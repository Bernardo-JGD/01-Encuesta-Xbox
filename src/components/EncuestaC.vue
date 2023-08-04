<template>
<div class="contenedorPrincipal" >
    <div class="contenedorElementos" >
        <!--Boton cerrar-->
        <div :class="{ 'contenedorCerrar': !regresar, 'contenedorCerrarRegresar':regresar }" >
            <a v-if="regresar"  >Regresar</a>
            <a>Cerrar</a>
        </div>

        <!--Titulo-->
        <div class="contenedorTituloDescripcion" >
            <titulo :tituloPosicion="tituloPosicion"/>
            <descripcion :descripcionPosicion="descripcionPosicion" :descripcionHabilitado="descripcionHabilitado"/>
        </div>

        <!-- Contenedor de cambio elementos-->
        <div class="" v-if="experienciaInicio"  >
            <experiencia @regresar-boton="btnRegresarVisible" @enviar-boton="btnEnviarVisible" @cambiar-titulo-descripcion="cambiarTituloDescripcion" />
        </div>

        <!-- Contenedor botones-->
        <div class="" v-if="salirJuego" >
            <botones-inicio-encuesta @respuesta-enviada="empezarEncuesta" />
        </div>

        <!--Enviar y  Cuentanos más -->
        <div class="contenedorBotonesEnviarYmas" v-if="experienciaInicio"  >
            <!-- Enviar -->
            <div  class="contenedorEnviar"  v-if="enviar" >
                <button :class="{ 'boton': !enviar, 'botonInhabilitado': enviar }" id="botonEnviar" :disabled="enviar" >Enviar</button>
            </div>

            <!-- Cuentanos mas -->
            <div class="contenedorCuentaMas" >
                <a>Cuéntanos más</a>
            </div>
        </div>

    </div>       
</div>
 

</template>

<script>
import Titulo from './TituloC.vue';
import Descripcion from './DescripcionC.vue';
import BotonesInicioEncuesta from './BotonesInicioEncuesta.vue';
import Experiencia from './ExperienciaC.vue';

export default{

    data: () => ({
        tituloPosicion: 0,
        descripcionPosicion: 0,
        descripcionHabilitado: true,
        salirJuego: true,
        experienciaInicio: false,
        enviar: true,
        regresar: false,
    }),
    components: {
        Titulo,
        Descripcion,
        BotonesInicioEncuesta,
        Experiencia
    },
    methods: {

        empezarEncuesta(salirJuego){
            this.salirJuego = salirJuego;
            this.tituloPosicion = 1;
            this.descripcionHabilitado = false;
            this.experienciaInicio = true;
            this.enviar = false;
        },
        
        btnRegresarVisible(){
            this.regresar = !this.regresar;
        },
        btnEnviarVisible(){
            this.enviar = true;
        },
        cambiarTituloDescripcion(tituloPosicion, descripcionPosicion){
            this.tituloPosicion = tituloPosicion;
            this.descripcionPosicion = descripcionPosicion;
            this.descripcionHabilitado = true;
        },
        btnEnviarHabilitado(){
            
        },
        regresarOpciones(){

        }


    }
}

</script>

<style scoped >



.contenedorElementos{
    background: #1A1B1E;
    border-radius: 5px;
    border: 1px solid black;
    width: 400px;
    padding: 2.5%;
}

.contenedorCerrar{
    display: flex;
    flex-direction: row-reverse;
}

.contenedorCerrarRegresar{
    display: flex;
    justify-content: space-between;
}

.contenedorTituloDescripcion{
    width: 100%;
    margin: 0 auto;
}

.contenedorBotonesEnviarYmas{
    width: 400px;
    margin-top: 1.8rem;
    display: flex;
    justify-content: center;
    align-items: center;
    flex-flow: row wrap;
}

.contenedorEnviar{
    width: 325px;
    display: flex;
    justify-content: center;
    padding: 0.8rem;
    margin: 4px 0px 4px 0px;
    
}

.contenedorCuentaMas{
    width: 300px;
    display: flex;
    justify-content: center;
    padding: 0.8rem;
    margin: 4px 0px 4px 0px;
    border-radius: 5px;
}


.contenedorCuentaMas:hover{
    background: #2d3036;
}

.boton{
    background: green;
    width: 100%;
    padding: 0.8rem;
    color: snow;
    font-size: 1rem;
    border-radius: 5px;
    border: 1px solid transparent;
    font-weight: bold;
}

.boton:hover{
    background: rgb(0, 165, 0);
    cursor: pointer;
}

.botonInhabilitado{
    background: rgba(0, 128, 0, 0.316);
    width: 100%;
    padding: 0.8rem;
    color: rgba(255, 250, 250, 0.472);
    font-size: 1rem;
    border-radius: 5px;
    border: 1px solid transparent;
    font-weight: bold;
}


</style>