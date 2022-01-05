<template>
  <div id="app">
    <input type="text" v-model="clienteAlisson.nome">
    <input type="text" v-model="clienteAlisson.email">
    <Cliente :cliente="clienteAlisson" :showAge="true"/>
    <Cliente :cliente="clienteAlisson" :showAge="false"/>
    <Cliente :cliente="clienteAlisson" :showAge="true"/>
  </div>
</template>

<script>
import Cliente from './components/Cliente.vue'
//import Produto from './components/Produto.vue'

export default {
  name: 'App',
  data(){
    return {
      postMalone: "I'm so fucking a Rockstar",
      clienteAlisson: {
          nome: "Alisson Andrade",
          email: "alisson-nagrade@outlook.com", 
          idade: "32"
      }
    }
  },
  components: {
    Cliente,
    //Produto
  }
}
</script>

<style>

</style>
