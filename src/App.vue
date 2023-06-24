<template>

  <CaracolaMagica />
</template>

<script>

//Se de be importar ese componente
import CaracolaMagica from './components/CaracolaMagica.vue'
export default {
  //Este componente se puede utilizar en diferentes paginas
  //Configurar la opcion components
  name: 'App',
  components: {
    CaracolaMagica
  },
}
</script>
<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>