<template>
  <header class="header">
    <h1>Slots</h1>
    <p>
      Os slots são uma maneira de passar conteúdo dinâmico de um componente pai
      para um componente filho. Eles permitem que você defina pontos de inserção
      no template de um componente filho, onde o conteúdo do componente pai pode
      ser injetado.
    </p>
    <p>Exemplo:</p>

    <p>
      1. A diretiva "v-slot:" com nome (v-slot:title) recebe o que está sendo
      passado no arquivo App.vue. Ele também possui um v-if para que se não ser
      injetado não seja exibido no DOM.
    </p>
    <h3 v-if="$slots.title" class="title">
      <slot name="title" />
    </h3>

    <p>2. Diretiva "v-slot:" com nome (v-slot:description) sem v-if</p>
    <div class="description">
      <slot name="description" />
    </div>

    <p>
      3. Slot sem nome, identificamos como default. Irá receber qualquer
      informação que estiver dentro da tag "TheSlot" pois não está sendo
      identificado no "v-slot:""
    </p>
    <div class="content">
      <slot />
    </div>
  </header>
</template>

<script>
export default {
  name: "TheSlot",
  mounted() {
    // console.log(this.$el);
    // console.log(this.$slots);
    console.log(this.$slots.description);
  },
};
</script>

<style>
.header {
  background-color: rgb(128, 163, 180);
  color: rgb(0, 0, 0);
}
</style>