<template>
  <div>
    Exemplo de scoped e global
    <BaseCard />
  </div>

  <div>
    <TheSlot>
      <template v-slot:title>
        Só é exibido se aqui não estiver vazio pois colocamos um
        v-if="$slots.title".
      </template>

      <template v-slot:description>
        <p>Alguma coisa</p>
      </template>

      Se eu colocar qualquer texto fora do v-slot: então entrará para a tag
      standard slot
    </TheSlot>

    <LifeCycle />

    <TheHeader v-if="showHeader" />

    <div v-show="showName">
      Nome: {{ firstName }} <br />
      Sobrenome: {{ lastName }}
    </div>

    <div v-if="accessLevel === 'admin'">Usuário Admin</div>
    <div v-else-if="accessLevel === 'marketing'">Usuário Marketing</div>
    <div v-else>Usuário comum</div>

    <!-- <img alt="Vue logo" src="./assets/logo.png" />
    <HelloWorld msg="Welcome to Your Vue.js App" /> -->
  </div>
</template>

<script>
// import HelloWorld from "./components/HelloWorld.vue";
import TheHeader from "./components/TheHeader.vue";
import LifeCycle from "./components/Life_Cycle/LifeCycle.vue";
import TheSlot from "./components/slot/TheSlot.vue";
import BaseCard from "./components/BaseCard.vue";
export default {
  name: "App",
  components: {
    // HelloWorld,
    TheHeader,
    LifeCycle,
    TheSlot,
    BaseCard,
  },
  data() {
    //Central de variáveis do componente
    return {
      showHeader: true,
      firstName: "John",
      lastName: "Snow",
      showName: false,
      accessLevel: "marketing",
    };
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  /* text-align: center; */
  color: #2c3e50;
  margin-top: 60px;
}
</style>

<!-- 
v-show -> exibe no DOM porém com display:none
v-if -> não exibe no DOM
v-bind: ou apenas ":" -> deixa os atributos dinâmicos
v-on:click="" ou apenas "@click=""" -> serve para pegar eventos de click por exemplo
Modificador evento -> Modifica o comportamento original do evento Ex.: .stop, .prevent, .self, .capture, .once, .passive
Pode ser verificado na documentação do vue: https://vuejs.org/guide/essentials/event-handling.html#event-modifiers
-->
