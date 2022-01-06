<template>
    <div :class="{'cliente': !isPremium, 'cliente-premium': isPremium}">
        <h4>Nome: {{cliente.nome}}</h4>
        <hr>
        <p>E-mail: {{cliente.email}}</p>
        <p v-if="showAge">Idade: {{cliente.idade}}</p>
        <p v-else>O usuário é corno e não quer exibir sua idade.</p>
        <button @click="changeClienteClass($event)">Mudar</button>
        <button @click="deleteClientEvent($event)">Deletar</button>
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
    }
}

</script>

<style scoped>
    .cliente{
        padding: 1%;
        background-color: darkgrey;
        margin: 10px;
        width: 500px;
        height: 180px;
    }

    .cliente-premium{
        padding: 1%;
        background-color: black;
        color: gold;
        margin: 10px;
        width: 500px;
        height: 180px;

    }
</style>