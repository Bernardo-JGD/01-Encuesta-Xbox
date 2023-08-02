<template>

<div class="contenedor" >
    <div class="opciones">
        <a>Buena</a>
    </div>
    <div class="opciones" >
        <a>Mala</a>
    </div>
</div>
    
</template>

<script>

export default{
    
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
}

.opciones:hover{
    background: #515863;
    cursor: pointer;
}

</style>