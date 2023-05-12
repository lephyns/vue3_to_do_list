<template>
    <div>
        <p>Exemplo componete beforeUnmount e unmounted que será ocultado quando clicado no botão</p>
    </div>
</template>

<script>
export default {
  name: "BeforeUnmount",
  mounted() {
    window.addEventListener('resize', this.resize);
  },
  beforeUnmount() {
    //Destruir libs, eventos, listeners, etc
    console.log('beforeUnmount');
    window.removeEventListener('resize', this.resize);
  },
  unmounted() {
    console.log('unmounted');
  },

  methods: {
    resize($evt) {
        console.log($evt)
    }
  }
}
</script>

<style scoped>
p {
    background-color: rgb(76, 189, 160);
    color: white;
}
</style>