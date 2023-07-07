<template>
    <h3>Contador</h3>
    <p>{{ numero }}</p>
  </template>
  
  <script>
  export default {
      name: "Contador1",
      data(){
          return{
              numero: 5
          }
      } ,
      methods:{
          obtenerCuadrado(){
              console.log("Entro al metodo cuadrado")
              return this.numero*this.numero
              
          }
      },
      computed:{
          obtenerCuadradoComputado(){
              console.log("Entro al metodo cuadrado")
              return this.numero*this.numero
          }
      }
  };
  </script>
  
  <style>
  </style>