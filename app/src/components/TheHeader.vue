<template>
  <div>
    <div>
      One-way data binding: quando o sistema exibe a informação ao usuário ex.:
      propriedade name: 'John Snow' <br />
      Two-way data binding: quando o usuário coloca a informação no input <br />
      v-model -> formulários
    </div>

    <br />
    <br />

    <div>
      <label for="">Nome</label><br>
      <input v-model="name" type="text" /><br>
      {{ name }}
    </div>

    <br>
    <br>

    <div>
      <label>Sports</label><br>
      <select v-model="sports">
        <option value="">Escolha</option>
        <option value="futebol">Futebol</option>
        <option value="skate">Skate</option>
        <option value="tenis">Tênis</option>
      </select><br>
      {{ sports }}
    </div>

    <br>
    <br>

    <div>
      <label>Newsletter</label><br>
      <input v-model="newsletter" type="radio" value="Sim">Sim
      <input v-model="newsletter" type="radio" value="Não">Não
      {{ newsletter }}
    </div>

    <br>
    <br>

    <div>
      <label>Contrato</label><br>
      <input v-model="contract" type="checkbox">Aceita nossos termos...<br>
      {{ contract }}
    </div>

    <br>
    <br>

    <div>
      <label>Cores que você mais gosta</label><br>
      <input v-model="colors" type="checkbox" value="azul">Azul
      <input v-model="colors" type="checkbox" value="amarelo">Amarelo<br>
      {{ colors }}
    </div>

    <br>
    <br>

    <!-- <h1 :class="classVar"> -->
    <h1 :class="{ title: true, 'title-home': isHome }">Curso Vue 3</h1>

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
      <img v-if="obj.imgSrc" :src="obj.imgSrc" />
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
      newsletter: '',
      name: 'John Snow',
      sports: '',
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
};
</script>

<style scoped>
.title {
  font-size: 20px;
  color: blue;
}
.title-home {
  font-size: 40px;
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