<template>
    <div :class="{'cliente': !isPremium, 'cliente-premium': isPremium}">
        <h4>Nome: {{cliente.nome | upperCase }}</h4>
        <hr>
        <p>E-mail: {{cliente.email}}</p>
        <p v-if="showAge">Idade: {{cliente.idade}}</p>
        <p v-else>O usuário é corno e não quer exibir sua idade.</p>
        <button @click="changeClienteClass($event)" class="button is-warning">Mudar</button>
        <button @click="deleteClientEvent($event)" class="button is-danger">Deletar</button>
        <h4>Id especial: {{specialId}}</h4>
    </div>
</template>

<script>
export default {
    data(){
        return {
            isPremium: false
        }
    },
    props: {
        cliente: Object,
        showAge: Boolean
    },
    methods: {
        changeClienteClass: function($event){
            console.log($event);
            this.isPremium = !this.isPremium;
        },
        deleteClientEvent: function(){
            this.$emit("deleteMe", {idCliente: this.cliente.id, component: this});
        }
    },
    filters: {
        upperCase: function(value){
            return value.toUpperCase();
        }
    },
    computed: {
        specialId: function () {
            return (this.cliente.email + this.cliente.nome + this.cliente.id).toUpperCase();
        }
    }
}

</script>

<style scoped>
    .cliente{
        padding: 1%;
        background-color: darkgrey;
        margin: 10px;
        width: 500px;
        height: 230px;
    }

    .cliente-premium{
        padding: 1%;
        background-color: black;
        color: gold;
        margin: 10px;
        width: 500px;
        height: 230px;

    }
</style>