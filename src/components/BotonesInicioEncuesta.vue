<template>

    <div class="contenedorBotones" >
        <a class="salir" @click="$emit('respuesta-enviada', false)" >
            Salir del juego
        </a>
        <a class="noImporta" >
            No importa
        </a>
    </div>

</template>

<script>

export default{
    
}

</script>


<style scoped >

.contenedorBotones{
    width: 400px;
    display: flex;
    justify-content: center;
    align-items: center;
    flex-flow: row wrap;
}

.salir{
    text-decoration: none;
    background: #c11010;
    color: snow;
    border-radius: 5px;
    padding: 0.8rem;
    margin: 0.4rem 0px 0.4rem 0px;
    width: 450px;
    text-align: center;
}

.noImporta{
    text-decoration: none;
    background-color: #2D3036;
    color: snow;
    border-radius: 5px;
    padding: 0.8rem;
    margin: 0.4rem 0px 0.4rem 0px;
    width: 450px;
    text-align: center;
}

.salir:hover{
    transition: 0.5s;
    background: #e81515;
    cursor: pointer;
}

.noImporta:hover{
    transition: 0.5s;
    background: #545a66;
    cursor: pointer;
}

</style>