<template>
  <div class="todoBox">
    <h3>todoMVC</h3>
    <add-button
      :todo="todo"
      v-on:onAddTodo="onAddTodo"
    ></add-button>
    <list
      :list="filterList"
      v-on:changeStatus="changeStatus"
    ></list>
    <p>
      filter:
      <span @click="onFilterChange($event)">all</span> |
      <span @click="onFilterChange($event)">active</span> |
      <span @click="onFilterChange($event)">completed</span>
    </p>
  </div>
</template>


<script>
export default {
  name: 'Todo',
  components: {
    'addButton': require('../components/AddButton.vue'),
    'List': require('../components/list.vue')
  },
  data () {
    return {
      todo: '',
      list: [],
      status: 'ALL'
    }
  },
  computed: {
    filterList () {
      const status = this.$data.status
      const list = this.$data.list
      if (status === 'ACTIVE') {
        return list.filter((item) => {
          return item.status === false
        })
      } else if (status === 'COMPLETED') {
        return list.filter((item) => {
          return item.status === true
        })
      } else {
        return list
      }
    }
  },
  methods: {
    onAddTodo (value) {
      this.todo = value
      this.list.push({
        text: this.todo,
        status: false
      })
      this.todo = ''
    },
    changeStatus (index) {
      this.list[index].status = !this.list[index].status
    },
    onFilterChange (e) {
      this.status = e.target.innerHTML.toUpperCase()
    }
  }
}
</script>
<style scoped>
ul {
  list-style-type: none;
}
.todoBox {
  margin: 0 auto;
  width: 300px;
}
</style>
