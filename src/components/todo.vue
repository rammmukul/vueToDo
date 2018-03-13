<template>
  <div class="todo" :class="{ isDone: data.isDone }">
      {{ data.title }}
  </div>
</template>

<script>
export default {
  name: "todo",
  props: ['data'],
  data() {
    return {}
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
