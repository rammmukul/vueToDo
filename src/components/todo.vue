<template>
  <div class="todo">
      {{ todoList.todo.title }}
  </div>
</template>

<script>
export default {
  name: "todo",
  data() {
    return {
      todoList: {
        todo: {
          title: "do this",
          isDone: false,
          timeStamp: 1520832857240
        }
      }
    };
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
