<template>
  <div id="app">
    <div v-for="todoList in todoLists">
      <div v-text="todoList.title"></div>
       <ul>
         <li v-for="todo in todoList.todos" :class="{isDone: todo.todo.isDone}">{{ todo.todo.title }}</li>
       </ul>
    </div>
    <hr>
    <todoList/>
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
              todo: {
                title: "do this",
                isDone: false,
                timeStamp: 1520832857240
              }
            },
            {
              todo: {
                title: "do that",
                isDone: false,
                timeStamp: 1520832857500
              }
            },
            {
              todo: {
                title: "do this too",
                isDone: true,
                timeStamp: 1520832857512
              }
            }
          ]
        },
        {
          title: "outDoors",
          todos: [
            {
              todo: {
                title: "do this",
                isDone: false,
                timeStamp: 1520832857240
              }
            },
            {
              todo: {
                title: "do that",
                isDone: false,
                timeStamp: 1520832857500
              }
            },
            {
              todo: {
                title: "do this too",
                isDone: true,
                timeStamp: 1520832857512
              }
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
