<template>
  <div id="app">
    <div id="sidebar"><div></div></div>
    <todoList v-for="todoList in todoLists" :key="todoList.title" :data="todoList">
    </todoList>
  </div>
</template>

<script>
import todoList from "./components/todoList";
import todo from "./components/todo";

export default {
  name: "App",
  components: {
    todoList,
    todo
  },
  data() {
    return {
      todoLists: [
        {
          title: "grocery",
          todos: [
            {
              id: '0',
              title: "do this",
              isDone: false,
              timeStamp: 1520832857240
            },
            {
              id: '1',
              title: "do that",
              isDone: true,
              timeStamp: 1520832857240
            },
            {
              id: '2',
              title: "do this too",
              isDone: false,
              timeStamp: 1520832857240
            }
          ]
        }
      ]
    };
  }
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
