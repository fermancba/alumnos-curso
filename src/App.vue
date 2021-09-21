<template>
  <div id="app">
    <buscador />
    <todo-list />
  </div>
</template>

<script>
import TodoList from "./components/TodoList.vue";
import Buscador from "./components/Buscador.vue";

export default {
  name: "App",
  components: {
    TodoList,
    Buscador
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
