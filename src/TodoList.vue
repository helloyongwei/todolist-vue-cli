<template>
  <div>
    <div>
      <input type="text" v-model="inputValue">
      <button @click="handleClick">提交</button>
    </div>
    <ul>
      <todo-item
        v-for="(item, index)
         of
         lists"
        :key="index"
        :content="item"
        :index="index"
        @delete="handleDelete"
      ></todo-item>
    </ul>
  </div>
</template>

<script>
import TodoItem from './components/TodoItem.vue'
export default {
  data: function () {
    return {
      inputValue: '',
      lists: []
    }
  },
  components: {
    'todo-item': TodoItem
  },
  methods: {
    handleDelete (index) {
      this.lists.splice(index, 1)
    },
    handleClick () {
      this.lists.push(this.inputValue)
      this.inputValue = ''
    }
  }

}
</script>

<style>

</style>
