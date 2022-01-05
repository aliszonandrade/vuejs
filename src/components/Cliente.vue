<template>
    <div :class="{'cliente': !isPremium, 'cliente-premium': isPremium}">
        <h4>Nome: {{cliente.nome}}</h4>
        <hr>
        <p>E-mail: {{cliente.email}}</p>
        <p v-if="showAge">Idade: {{cliente.idade}}</p>
        <p v-else>O usuário é corno e não quer exibir sua idade.</p>
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
    }
}

</script>

<style scoped>
    .cliente{
        padding: 1%;
        background-color: darkgrey;
        margin: 10px;
        width: 500px;
        height: 140px;
    }

    .cliente-premium{
        padding: 1%;
        background-color: black;
        color: gold;
        margin: 10px;
        width: 500px;
        height: 140px;

    }
</style>