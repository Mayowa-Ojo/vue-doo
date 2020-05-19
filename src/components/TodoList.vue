<template>
  <div class="w-full bg-gray-100 h-full">
    <Todo 
      v-for="(todo, index) in todos" 
      v-bind:key="index" 
      v-bind:todo="todo" 
      @toggleComplete="$emit('toggleComplete', $event)"
      @deleteTodo="$emit('deleteTodo', $event)"
      @editTodo="$emit('editTodo', $event)"
    />
  </div>
</template>

<script>
import Todo from "./Todo.vue"

export default {
  name: 'TodoList',
  components: {
    Todo
  },
  props: ["todos"]
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss" scoped>

</style>
