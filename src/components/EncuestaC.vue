<template>
<div class="contenedorPrincipal" >
    <div class="contenedorElementos" >
        <!--Boton cerrar-->
        <div :class="{ 'contenedorCerrar': !regresar, 'contenedorCerrarRegresar':regresar }" >
            <div v-if="regresar" @click="componentesEncuestaDecremento(), cambiarEstadosComponentes()" class="btnRegresar" >
                <a  >Regresar</a>
            </div>
            <div>
                <a>Cerrar</a>
            </div>
        </div>

        <!--Titulo-->
        <div class="contenedorTituloDescripcion" >
            <titulo :tituloPosicion="tituloPosicion"/>
            <descripcion :descripcionPosicion="descripcionPosicion" :descripcionHabilitado="descripcionHabilitado"/>
        </div>

        <!-- Contenedor de cambio elementos-->
        <div class="" v-if="experienciaInicio"  >
            <experiencia @enviar-boton="btnEnviarVisible"
                         @cambiar-titulo-descripcion="cambiarTituloDescripcion"
                         @componentes-encuesta-incremento="componentesEncuestaIncremento"
                         @cambiar-estados-componentes="cambiarEstadosComponentes"
                         :habilitarBotonesExperiencia="habilitarBotonesExperiencia"
                         :habilitarComponentesExperiencia="habilitarComponentesExperiencia"
                         :habilitarExperienciaBuena="habilitarExperienciaBuena"
                         :habilitarExperienciaMala="habilitarExperienciaMala"
                         :habilitarExperienciaBuenaBotones="habilitarExperienciaBuenaBotones"
                         :habilitarExperienciaMalaBotones="habilitarExperienciaMalaBotones"
                         :habilitarComponenteRespuestas="habilitarComponenteRespuestas"
            />
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
        encuestaComponentesContador: 0,
        experienciaBuenaMalaActual: -1,
        habilitarBotonesExperiencia: true,
        habilitarComponentesExperiencia: false,
        habilitarExperienciaBuena: false,
        habilitarExperienciaMala: false,
        habilitarExperienciaBuenaBotones: false,
        habilitarExperienciaMalaBotones: false,
        habilitarComponenteRespuestas: false,
        
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
        btnEnviarVisible(habilitar){
            this.enviar = habilitar;
        },
        cambiarTituloDescripcion(tituloPosicion, descripcionPosicion, descripcionHabilitado){
            this.tituloPosicion = tituloPosicion;
            this.descripcionPosicion = descripcionPosicion;
            this.descripcionHabilitado = descripcionHabilitado;
        },
        componentesEncuestaIncremento(){
            this.encuestaComponentesContador++;
        },
        componentesEncuestaDecremento(){
            this.encuestaComponentesContador--;
            console.log("Contador: " + this.encuestaComponentesContador);
        },
        cambiarEstadosComponentes(experienciaBuenaMala){
            //btnEnviar
            //Titulos
            //Descripcion
            //Tendrán que ser cambiados desde estos estados
            if(this.encuestaComponentesContador === 0){
                console.log("Caso 0");
                this.regresar = false;
                this.habilitarBotonesExperiencia = true;
                this.habilitarComponentesExperiencia = false;
                this.cambiarTituloDescripcion(1, 0, false);
                this.btnEnviarVisible(false);
            }
            if(this.encuestaComponentesContador === 1){
                this.regresar = true;
                console.log("caso 1");
                this.habilitarBotonesExperiencia = false;
                this.habilitarComponentesExperiencia = true;
                if(experienciaBuenaMala === 0){//0 experiencia buena
                    this.experienciaBuenaMalaActual = experienciaBuenaMala;
                    this.habilitarExperienciaBuena = true;
                    this.habilitarExperienciaBuenaBotones = true;
                }
                if(experienciaBuenaMala === 1){//1 experiencia mala
                    this.experienciaBuenaMalaActual = experienciaBuenaMala;
                    this.habilitarExperienciaMala = true;
                    this.habilitarExperienciaMalaBotones = true;
                }
            }

            if(this.encuestaComponentesContador === 2){
                console.log("Caso 2");
                if(this.experienciaBuenaMalaActual === 0){//Experiencia buena
                    this.habilitarExperienciaBuenaBotones = false;
                    this.habilitarComponenteRespuestas = true;
                }
                if(this.experienciaBuenaMalaActual){//Experiencia mala
                    this.habilitarExperienciaMalaBotones = false;
                    this.habilitarComponenteRespuestas = true;
                }
                
            }

            if(this.encuestaComponentesContador === 3){
                console.log("caso 3");
            }

            console.log(`regresar ${this.regresar}`);
            console.log(`habilitarBotonesExperiencia ${this.habilitarBotonesExperiencia}`);
            console.log(`habilitarComponentesExperiencia ${this.habilitarComponentesExperiencia}`);
            console.log(`habilitarExperienciaBuena ${this.habilitarExperienciaBuena}`);
            console.log(`habilitarExperienciaBuenaBotones ${this.habilitarExperienciaBuenaBotones}`);
            console.log(`habilitarExperienciaBuena ${this.habilitarExperienciaMala}`);
            console.log(`habilitarExperienciaBuenaBotones ${this.habilitarExperienciaMalaBotones}`);
            console.log(`habilitarComponenteRespuestas ${this.habilitarComponenteRespuestas}`);
            console.log("");
            console.log(`experienciaBuenaMala ${experienciaBuenaMala}`);
            console.log(this.encuestaComponentesContador);
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

.btnRegresar{
    padding: 0.5rem;
    border-radius: 5px;
}

.btnRegresar:hover{
    background: #515863;
    cursor: pointer;
}

</style>