<template>
  <img alt="Vue logo" src="./assets/logo.png">
  <Calculadora></Calculadora>

</template>

<script>
import Contador from './components/Contador.vue'
import Calculadora from './components/Calculadora.vue'
export default {
  name: 'App',
  components: {
    Calculadora
  }
}
</script>