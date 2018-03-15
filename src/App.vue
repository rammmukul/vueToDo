<template>
  <div id="app">
    <div id="sidebar">
      <h1>Todos</h1>
      <input type="text" v-model="newTodoListTitle" v-on:keyup.enter="add" placeholder="Add a todoList"/>
      <button v-on:click="add()" >add</button>
    </div>
    <todoList v-for="todoList in todoLists" 
      :key="todoList.title" 
      :data="todoList" 
      @addTodo="addTodo"
      @updateState="updateState" 
      @removeTodo="removeTodo"
      @removeTodoList="removeTodoList">
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
      newTodoListTitle: '',
      todoLists: [
        {
          title: "grocery",
          todos: [
            {
              title: "do this",
              isDone: false,
              timeStamp: 1520832857240
            },
            {
              title: "do that",
              isDone: true,
              timeStamp: 1520832857240
            },
            {
              title: "do this too",
              isDone: false,
              timeStamp: 1520832857240
            }
          ]
        }
      ]
    };
  },
  methods: {
    add() {
      if (!this.newTodoListTitle) {
        return 1
      }
      if (this.todoLists.filter(e => e.title === this.newTodoListTitle).length!==0) {
        return 1
      }
      let newTodoList = {
        title: this.newTodoListTitle,
        todos: []
      }
      this.todoLists.push(newTodoList)
      this.newTodoTitle = ''
      console.log('App addTodoList', newTodoList)
    },
    addTodo (todo) {
      console.log('App addTodo', todo)
    },
    updateState (todo) {
      console.log('App updateState', todo)
    },
    removeTodo (todo) {
      console.log('App remove', todo)
    },
    removeTodoList (todoList) {
      console.log('App got "remove" with', todoList)
      this.todoLists = this.todoLists.filter(e => e.title !== todoList)
    }
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
