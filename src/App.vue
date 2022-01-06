<template>
  <div id="app">
    <h3>Cadastro clientola: </h3>
    <small v-show="erro" id="nomeErro">Nome inválido!</small><br>
    <input type="text" placeholder="Nome" v-model="nomeField"><br>
    <input type="text" placeholder="E-mail" v-model="emailField"><br>
    <input type="number" placeholder="Idade" v-model="idadeField">
    <button @click="registerCustomer">Cadastrar</button>
    <hr>
    <div v-for="(cliente,index) in clientes" :key="cliente.id">
      <h3>{{index+1}}</h3>
      <Cliente :cliente="cliente" :showAge="true" @deleteMe="deleteCustomer($event)"/>
      <h4>Edição: </h4>
      <input type="text" v-model="cliente.nome">
      <input type="text" v-model="cliente.email">
      <hr>
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
      erro: false,
      nomeField: "",
      emailField: "",
      idadeField: 0,
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
  },
  methods: {
    registerCustomer: function(){
      if(this.nomeField == "" || this.nomeField == " " || this.nomeField.length < 3){
        this.erro = true;
      }else{
        this.clientes.push({
        id: Object.keys(this.clientes).length + 1,
        nome: this.nomeField,
        email: this.emailField,
        idade: this.emailField
      })

      this.nomeField = "";
      this.emailField = "";
      this.idadeField = 0;
      this.erro = false;
      }
    },
    deleteCustomer: function($event){
      var newArray = this.clientes.filter(cliente => cliente.id != $event.idCliente);
      this.clientes = newArray;
    }
  }
}
</script>

<style>
  #nomeErro{
    color:red;
  }
</style>
