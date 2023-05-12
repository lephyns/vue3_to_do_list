<template>
  <div>
    <h1>Ciclo de vida (life cycle)</h1>
    <p>
      Fases do ciclo de vida do VueJs.<br />
      São 4: a criação, a montagem, a atualização e a desmontagem.
    </p>

    <br />

    <h3>Criação</h3>
    <ul>
      <li>Preparar o componente</li>
      <li>Ajax, inicializar algumas variáveis</li>
      <li>Não tem acesso ao template (DOM)</li>
    </ul>

    <br />
    
    <h3>Montagem</h3>
    <ul>
      <li>Inicializar uma lib externa (new lib())</li>
      <li>Precisa de acesso ao template (DOM)</li>
      <li>Tem acesso ao template (DOM)</li>
    </ul>

    <br />

    <h3>Atualização</h3>
    <ul>
      <li>Debug</li>
      <li>Update</li>
    </ul>

    <br />

    <h3>Desmontagem</h3>
    <ul>
      <li>
        Remover tudo o que for necessário para liberar memória (lib>destroy())
      </li>
    </ul>

    <br />

    <h4>HOOKS que interagem com as fases descritas acima</h4>
    <ul>
      <li>
        beforeCreate() {} -> Antes do componente ser criado (LifeCycle.vue)
      </li>
      <li>created() {} -> Quando o componente foi criado (LifeCycle.vue)</li>
      <li>
        beforeMount() {} -> Antes do componente ser montado (LifeCycle.vue)
      </li>
      <li>
        mounted() {} - Quando o componente foi montado (BeforeUnmount.vue)
      </li>
      <li>
        beforeUnmount() {} -> Antes do componente ser desmontado
        (BeforeUnmount.vue)
      </li>
      <li>
        unmounted() {} -> Quando o componente foi desmontado (BeforeUnmount.vue)
      </li>
      <li>
        beforeUpdate() {} -> Antes do compontente atualizar (LifeCycle.vue)
      </li>
      <li>
        updated() {} -> Quando o componente foi atualizado (LifeCycle.vue)
      </li>
    </ul>
    <br />

    <div>
      <h4>Hello world</h4>

      <p>
        Quando alterado o valor do input abaixo é acionado os hooks
        beforeUpdate() e updated()
      </p>
      <input v-model="name" type="text" />
      {{ name }}

      <br /><br />

      <p>
        Quando clicado no botão abaixo é acionado os hooks beforeUpdate() e
        updated()
      </p>
      <BeforeUnmount v-if="showHeader2" />
      <button @click="showHeader2 = !showHeader2">
        Ativar e desativar header
      </button>

      <p>Os demais hooks é possível verificar através do console</p>
    </div>

    <br />
    <br />
    <br />
  </div>
</template>

<script>
import BeforeUnmount from "../components/BeforeUnmount.vue";

export default {
  name: "LifeCycle",
  components: {
    BeforeUnmount,
  },
  data() {
    return {
      name: "John Snow",
      showHeader2: true,
    };
  },
  beforeUpdate() {
    //Utilizado mais para debuggar
    console.log("beforeUpdate", this.name);
  },
  updated() {
    //Utilizado mais para debuggar
    console.log("updated", this.name);
  },
  beforeCreate() {
    console.log("beforeCreate");
    console.log("Estado:", this.name); //Não tem acesso ao estado
    console.log("DOM", this.$el); //Não tem acesso ao DOM
  },
  created() {
    console.log("created");
    console.log("Estado:", this.name); //Tem acesso ao estado
    console.log("DOM", this.$el); //Não tem acesso ao DOM
  },
  beforeMount() {
    console.log("beforeMount");
    console.log("Estado:", this.name); //Tem acesso ao estado
    console.log("DOM", this.$el); //Não tem acesso ao DOM
  },
  mounted() {
    console.log("mounted");
    console.log("Estado:", this.name); //Tem acesso ao estado
    console.log("DOM", this.$el); //Tem acesso ao DOM
  },

  watch: {},

  computed: {},

  methods: {},
};
</script>