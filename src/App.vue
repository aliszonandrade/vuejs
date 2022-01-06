<template>
  <div id="app">
    <div v-for="(cliente,index) in clientes" :key="cliente.id">
      <h3>{{index+1}}</h3>
      <Cliente :cliente="cliente" :showAge="true"/>
      <hr>
      <h4>Edição: </h4>
      <input type="text" v-model="cliente.nome">
      <input type="text" v-model="cliente.email">
    </div>
    
  </div>
</template>

<script>
import Cliente from './components/Cliente.vue'
//import Produto from './components/Produto.vue'

export default {
  name: 'App',
  data(){
    return {
      clientes: [
        {
          id: 1,
          nome: "Alisson Nagrade",
          email: "alisson-nagrade@outlook.com", 
          idade: "23"
        },
        {
          id: 2,
          nome: "Alisson Andrade",
          email: "alisson-andrade@outlook.com", 
          idade: "12"
        },
        {
          id: 3,
          nome: "Alisson Ambrósio",
          email: "alisson-ambrosio@outlook.com", 
          idade: "32"
        }

      ]        
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
