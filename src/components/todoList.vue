<template>
  <div class="todoList">
    {{ data.title }}
    <button class="remove" v-on:click="remove">x</button>
    <ul>
      <li is="todo"
        v-for="todo in data.todos"
        :key="todo.title" 
        :data="todo" 
        @updateState="updateState($event)"
        @remove="removeTodo($event)">
      </li>
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
      let NewTodo = {
        title: this.newTodoTitle,
        isDone: false,
        timeStamp: Date.now()
      }
      this.data.todos.push(NewTodo)
      this.newTodoTitle = ''
      this.$emit('addTodo', [this.data.title, NewTodo])
    },
    updateState (todo) {
      this.$emit('updateState', [this.data.title, todo])
    },
    removeTodo (todo) {
      this.data.todos = this.data.todos.filter(e => e.title !== todo)
      this.$emit('removeTodo', [this.data.title, todo])
    },
    remove () {
      this.$emit('removeTodoList', this.data.title)
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
