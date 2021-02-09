<template>
  <main>
    <Header
      :themeIcon="themeIcon"
      :themeImage="themeImage"
      @toggleTheme="toggleThemeMode"
    ></Header>
    <form class="form" @submit="submitForm">
      <div class="form-control">
        <input ref="input" required type="text" id="input" />
      </div>
    </form>

    <article class="todo-wrap">
      <Todo
        v-for="item in todoData"
        :itemName="item.name"
        :key="item.id"
        :id="item.id"
      />
    </article>
  </main>
</template>

<script>
import Header from "./components/Header";
import Todo from "./components/Todo";
import moon from "./assets/images/icon-moon.svg";
import sun from "./assets/images/icon-sun.svg";
import bgDark from "./assets/images/bg-desktop-dark.jpg";
import bgLight from "./assets/images/bg-desktop-light.jpg";

export default {
  name: "App",
  components: {
    Header,
    Todo,
  },

  data() {
    return {
      todoData: [],
      themeIcon: moon,
      isLightTheme: true,
      themeImage: bgLight,
    };
  },
  methods: {
    toggleThemeMode() {
      this.isLightTheme = !this.isLightTheme;
      this.isLightTheme ? (this.themeIcon = moon) : (this.themeIcon = sun);
      this.isLightTheme
        ? (this.themeImage = bgLight)
        : (this.themeImage = bgDark);
      document.querySelector("#app").classList.toggle("dark-scheme");
    },
    submitForm(e) {
      e.preventDefault();

      let newTodo = {
        id: new Date().getTime().toString(),
        name: this.$refs.input.value,
        completed: false,
      };
      this.todoData.push(newTodo);
      e.target.reset();
    },
  },
};
//  todoData: localStorage.getItem("tomTodo")
//         ? JSON.parse(localStorage.getItem("tomTodo"))
//         : [],
</script>

<style>
#app {
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
</style>
