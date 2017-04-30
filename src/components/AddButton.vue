<template>
  <div>
    <input ref="input" v-model="todo" type="text">
    <button @click="onChange">添加</button>
  </div>
</template>
<script>
export default {
  name: 'addbutton',
  props: ['todo', 'onAddTodo'],
  methods: {
    onChange () {
      this.$emit('onAddTodo', this.$refs.input.value)
    }
  }
}
</script>
<style scoped>
</style>
