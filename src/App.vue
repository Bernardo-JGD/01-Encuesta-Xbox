<template>

  <div  >
    <RouterView />
  </div>

  
</template>

<script >
import { RouterView } from 'vue-router';

export default{

  components: {
    RouterView
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

</style>