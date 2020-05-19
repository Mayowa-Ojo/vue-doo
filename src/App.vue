<template>
  <div id="app" class="bg-white border border-gray-300 border-solid mx-auto mt-24 overflow-auto rounded shadow-xs flex flex-col">
    <Form @addTodo="addTodo" />
    <TodoList 
      v-bind:todos="todos"
      @toggleComplete="toggleComplete"
      @deleteTodo="deleteTodo"
      @editTodo="editTodo"
    />
  </div>
</template>

<script>
import TodoList from './components/TodoList.vue'
import Form from './components/Form.vue'

const data = [
  { id: 1, text: "reate kanban board", completed: false },
  { id: 2, text: "post on dev.to", completed: true },
  { id: 3, text: "update trello board", completed: true },
  { id: 4, text: "create github gist", completed: true },
  { id: 5, text: "merge pull requests", completed: false },
  { id: 6, text: "start UI design templates", completed: true },
  { id: 7, text: "check slack messages", completed: false },
]

export default {
  name: 'App',
  components: {
    TodoList,
    Form
  },
  data: function() {
    return {
      todos: data
    }
  },
  methods: {
    toggleComplete: function(id) {
      this.todos = this.todos.map(todo => {
        if(todo.id == id) {
          return {...todo, completed: !todo.completed}
        }

        return {...todo}
      })
    },
    deleteTodo: function(id) {
      this.todos = this.todos.filter(todo => todo.id != id)
    },
    addTodo: function(data) {
      const id = this.todos[this.todos.length - 1].id + 1
      this.todos = [...this.todos, { id: id, text: data, completed: false }]
    },
    editTodo: function(data) {
      this.todos = this.todos.map(todo => {
        if(todo.id == data.id) {
          return {...data}
        }

        return {...todo}
      })
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  width: 22rem;
  height: 22rem;
}
</style>
