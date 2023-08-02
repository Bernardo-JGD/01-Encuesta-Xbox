<template>
<div class="contenedorPrincipal" >
    <div class="contenedorLogin" >
        <!-- Titulo -->
        <div class="centrarElementos" >
            <h2>Login</h2>
        </div>
        <!-- Formulario -->
        <div class="centrarElementos" >
            <form @submit.prevent="" >
                
                <div class="" >
                    <label class="" >Correo electrónico</label>
                    <input class="" type="email" placeholder="jefe_maestro@outlook.com" />
                </div>
                
                <div class="" >
                    <label class="" >Contraseña</label>
                    <input class="" type="password" />
                </div>

                <div class="" >
                    <a @click="activarRequisitos" class="requisitosContra" >Requisitos contraseña</a>
                    <ul class="" v-if="mostrarRequisitos" >
                        <li>Minimo 8 caracteres</li>
                        <li>Mayúsculas y minúsculas</li>
                        <li>Numeros y caracteres especiales</li>
                    </ul>
                </div>

                <div class="centrarElementos" >
                    <button>Ingresar</button>
                </div>
                
            </form>
        </div>
    </div>

</div>

</template>


<script>

export default{
    data: () => ({
        mostrarRequisitos: false,
    }),
    methods: {
        activarRequisitos(){
            this.mostrarRequisitos = !this.mostrarRequisitos;
        }
    }
}

</script>

<style scoped >

.contenedorPrincipal{
    border: 2px solid green;
    width: 100%;
    height: 100vh;
    display: flex;
    justify-content: center;
    align-items: center;
}

.contenedorLogin{
    border: 2px solid seashell;
    width:35%;
}

.centrarElementos{
    width: 100%;
    display: flex;
    justify-content: center;
}


.requisitosContra{
    color: green;
    font-size: 15px;
    text-decoration: underline;
}

.requisitosContra:hover{
    color: rgb(0, 162, 0);
    font-size: 15px;
    text-decoration: underline;
    cursor: pointer;
}

li{
    font-size: 12px;
}

label, input, a, button{
    width: 100%;
    margin: 10px 0px 10px 0px;
    font-size: 1rem;
    padding: 0.4em;
    outline: none;
}

.contenedorCampos{
    display: flex;
}

button{
    background: green;
    color: snow;
    padding: 0.8rem;
    border-radius: 5px;
    border: 1px solid transparent;
    font-weight: bold;
}

button:hover{
    background: rgb(0, 165, 0);
}

</style>