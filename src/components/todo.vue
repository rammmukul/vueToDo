<template>
  <div class="todo" :class="{ isDone: data.isDone }">
      <input type="checkbox" :checked="data.isDone" v-on:change="updateState" >
      {{ data.title }}
      <span class="controls">
        <span class="time">{{ Math.floor((Date.now() - data.timeStamp)/86400000) }} days</span>
        <button class="remove" v-on:click="remove">x</button>
      </span>
  </div>
</template>

<script>
export default {
  name: "todo",
  props: ["data"],
  data() {
    return {};
  },
  methods: {
    updateState() {
      this.data.isDone = !this.data.isDone;
    },
    remove () {
      console.log('todo remove', this.data.title)
      this.$emit('remove', this.data.title)
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
