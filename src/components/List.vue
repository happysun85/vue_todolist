<template>
  <ul>
    <li
      v-for="(item, index) in list"
      v-bind:id=index
      v-bind:class="{completed : item.status}"
      @click="onChangeStatus(index)"
    >
      {{item.text}},
    </li>
  </ul>
</template>
<script>
export default {
  name: 'tempName',
  props: ['list', 'changeStatus'],
  data: {
    thoughLine: 'text-decoration: line-through'
  },
  methods: {
    onChangeStatus (index) {
      this.$emit('changeStatus', index)
    }
  }
}
</script>
<style scoped>
.completed {
  text-decoration: line-through
}
</style>
