<template>

    <div class="contenedor" >
        <div class="opciones" >
            <a>Juego</a>
        </div>
        <div class="opciones" >
            <a>Streaming</a>
        </div>
    </div>

</template>

<script>

export default{

}

</script>


<style scoped >

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