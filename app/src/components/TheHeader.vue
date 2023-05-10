<template>
  <div>
    <h1>Eventos</h1>

    <p>
      v-on:click="" ou apenas "@click=""" é uma diretiva de escuta de eventos,
      neste caso para lidar com o evento de clique
    </p>

    <h4>@click escuta o evento de click no botão</h4>
    <button @click="onClick">Enviar</button>

    <br />
    <br />

    <h4>Escuta o evento de mouse over e mouse out</h4>
    <button @mouseover="onMouseover" @mouseout="onMouseOut">Mouse over</button>

    <br />
    <br />

    <h4>
      Escuta o evento do submit que irá redirecionar para uma URL quando clicado
    </h4>
    <form action="https://google.com" @submit="onSubmit">
      <button type="submit">Enviar para Google</button>
    </form>

    <br />
    <br />

    <h4>
      Escuta o evento Key up (quando soltar a tecla irá registrar no console o
      KeyboardEvent)
    </h4>
    <input type="text" @keyup="onKeyUp" />

    <br />
    <br />

    <h1>Modificadores de evento</h1>

    <p>
      Modifica o comportamento original do evento Ex.: .stop, .prevent, .self,
      .capture, .once, .passive <br />
      Pode ser verificado na documentação do vue:
      https://vuejs.org/guide/essentials/event-handling.html#event-modifiers
    </p>

    <h4>@click com modificador (.once)</h4>
    <button @click.once="onClick">Enviar</button>

    <br />
    <br />

    <h4>
      Evento de submit com modificador (.prevent), não irá redirecionar para a
      URL
    </h4>
    <form action="https://google.com" @submit.prevent="onSubmit">
      <button type="submit">Enviar para Google</button>
    </form>

    <br />
    <br />

    <h4>Escuta o evento da tecla enter (.enter)</h4>
    <input type="text" @keyup.enter="onKeyUp" />

    <br />
    <br />

    <h1>v-model</h1>
    <p>
      One-way data binding: quando o sistema exibe a informação ao usuário ex.: propriedade name: 'John Snow'
    </p>
    <p>Two-way data binding: quando o usuário coloca a informação no input</p>
    <p>v-model: é uma diretiva usada em formulários, dentro do input, textarea, checkbox, radio button, entre outros. Foi usado nos exemplos abaixo:</p>

    <br />
    <br />

    <div>
      <label>Nome</label><br />
      <input v-model="name" type="text" /><br />
      {{ name }}
    </div>

    <br />
    <br />

    <div>
      <label>Sports</label><br />
      <select v-model="sports">
        <option value="">Escolha</option>
        <option value="futebol">Futebol</option>
        <option value="skate">Skate</option>
        <option value="tenis">Tênis</option></select
      ><br />
      {{ sports }}
    </div>

    <br />
    <br />

    <div>
      <label>Newsletter</label><br />
      <input v-model="newsletter" type="radio" value="Sim" />Sim
      <input v-model="newsletter" type="radio" value="Não" />Não
      {{ newsletter }}
    </div>

    <br />
    <br />

    <div>
      <label>Contrato</label><br />
      <input v-model="contract" type="checkbox" />Aceita nossos termos...<br />
      {{ contract }}
    </div>

    <br />
    <br />

    <div>
      <label>Cores que você mais gosta</label><br />
      <input v-model="colors" type="checkbox" value="azul" />Azul
      <input v-model="colors" type="checkbox" value="amarelo" />Amarelo<br />
      {{ colors }}
    </div>

    <br />
    <br />


    <h1>
      Atributos dinâmicos
    </h1>


    <!-- <h1 :class="classVar"> -->
    <h5 :class="{ title: true, 'title-home': isHome }">Curso Vue 3</h5>

    <!-- <p :class="['text', {'text-home': isHome}]"> -->
    <p :class="pClass">
      Lorem ipsum dolor sit amet consectetur adipisicing elit. Exercitationem
      distinctio molestiae nemo illo voluptatum molestias laudantium quis quo
      magni, esse consectetur consequuntur, sapiente consequatur dolores
      pariatur dolorum. Consectetur, quidem nihil.
    </p>

    <!-- <p :style="{ 'color': 'orange', 'background-color': 'black' }"> -->
    <p :style="styleClass">
      Lorem ipsum dolor sit amet consectetur adipisicing elit. Culpa sequi
      saepe, harum minima ratione commodi consectetur provident nesciunt, sunt
      odio et voluptatibus maxime quasi praesentium possimus quo soluta quae
      adipisci.
    </p>

    <div v-for="(obj, index) in todos" :key="obj.id" class="todos-item">
      <img v-if="obj.imgSrc" :src="obj.imgSrc" alt="Imagem gatinho" />
      {{ index }} - {{ obj.title }}
    </div>
  </div>
</template>

<script>
export default {
  name: "App",
  data() {
    return {
      colors: [],
      contract: false,
      newsletter: "",
      name: "John Snow",
      sports: "",
      isHome: true,
      styleClass: {
        color: "orange",
        backgroundColor: "black",
        "font-size": "20px",
      },
      classVar: "title",
      pClass: ["text", "text-home"],
      imgAlt: "Foto de um gatinho",
      todos: [
        {
          userId: 1,
          id: 1,
          title: "delectus aut autem",
          completed: false,
          imgSrc: "http://placekitten.com/200/300",
        },
        {
          userId: 1,
          id: 2,
          title: "quis ut nam facilis et officia qui",
          completed: false,
          imgSrc: "http://placekitten.com/200/300",
        },
        {
          userId: 1,
          id: 3,
          title: "fugiat veniam minus",
          completed: false,
        },
        {
          userId: 1,
          id: 4,
          title: "et porro tempora",
          completed: true,
        },
        {
          userId: 1,
          id: 5,
          title:
            "laboriosam mollitia et enim quasi adipisci quia provident illum",
          completed: false,
        },
      ],
    };
  },
  methods: {
    //Aqui ficam todas as funções que vão ser criadas para o componente para fazer qualquer rotina de programação
    onClick($evt) {
      console.log("click", $evt);
    },
    onMouseover($evt) {
      console.log("Mouse over", $evt);
    },
    onMouseOut($evt) {
      console.log("Mouse out", $evt);
    },
    onSubmit($evt) {
      console.log("Submit", $evt);
    },
    onKeyUp($evt) {
      console.log("Key up", $evt);
    },
  },
};
</script>

<style scoped>
.title {
  font-size: 20px;
  color: blue;
}
.title-home {
  font-size: 20px;
  color: green;
}
.text {
  color: yellow;
}
.text-home {
  color: rgb(44, 137, 165);
}
.todos-item {
  background-color: #000;
  margin: 0 0 5px 0;
  padding: 3px 6px;
  color: #fff;
}
</style>