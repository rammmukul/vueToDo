<template>
  <div class="todoList">
  </div>
</template>

<script>
import todo from './todo'
import Vue from 'vue'

Vue.component('todo', todo)

export default {
  name: 'todoList',
  data () {
    return {
      todoList: todo
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
