<template>
  <div class="todoList">
    {{ data.title }}
    <ul>
      <li is="todo" v-for="todo in data.todos" :key="todo.title" :data="todo"></li>
    </ul>
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
    return {}
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
