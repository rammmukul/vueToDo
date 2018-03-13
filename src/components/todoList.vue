<template>
  <div class="todoList">
    {{ data.title }}
    <ul>
      <li is="todo" v-for="todo in data.todos" :key="todo.title" :data="todo" @remove="removeTodo($event)"></li>
    </ul>
    <input type="text" v-model="newTodoTitle" v-on:keyup.enter="add" placeholder="Add a todo"/>
    <button v-on:click="add()" >add</button>
  </div>
</template>

<script>
import todo from "./todo"
import Vue from "vue"

Vue.component("todo", todo)

export default {
  name: "todoList",
  props: ['data'],
  data() {
    return {
      newTodoTitle:''
    }
  },
  methods: {
    add() {
      if (!this.newTodoTitle) {
        return 1
      }
      if (this.data.todos.filter(e => e.title === this.newTodoTitle).length!==0) {
        return 1
      }
      this.data.todos.push({
        title: this.newTodoTitle,
        isDone: false,
        timeStamp: Date.now()
      })
      this.newTodoTitle = ''
    },
    removeTodo (todo) {
      console.log('got "remove" with', todo)
      this.data.todos = this.data.todos.filter(e => e.title !== todo)
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
