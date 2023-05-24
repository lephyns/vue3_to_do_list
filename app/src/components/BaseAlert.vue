<template>
    <div :class="baseClass">
        Seu formulário foi enviado com sucesso!
        <button @click="onClick()">X</button>
    </div>
</template>

<script>
export default {
    props: { //Propriedades que vamos passar do componente pai para o componente filho
    variant: {
        type: String,
        default: ''
    }
    },
    computed: { //
        baseClass() {
            return [
                'alert',
                this.variant ? `alert-${this.variant}` : ''
            ]
        }
    },
    methods: {
        onClick() {
            this.$emit('close')
            console.log('clicou')
        }
    }
}
</script>

<style scoped>
.alert {
    display: flex;
    justify-content: space-between;
    padding: 5px;
    border-radius: 6px;
    color: grey;
    background: #ddd;
}

.alert-success {
    background: #42b983;
    color: #fff;
}

.alert-danger {
    background: red;
    color: #fff;
}
</style>