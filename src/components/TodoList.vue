<template>
  <div class="todo-list clearfix">
    <todo v-on:toggle-status="toggleTodoStatus" v-on:delete-todo="deleteTodo" v-for="todo in todos" v-bind:todo="todo" :key="todo.id"></todo>
  </div>
</template>

<script type="text/javascript">

  import Todo from './Todo.vue'

  export default {
    props: ['todos'],
    components: {
      Todo
    },
    methods: {
      deleteTodo (todo) {
        const todoIndex = this.todos.indexOf(todo)
        this.todos.splice(todoIndex, 1)
      },
      toggleTodoStatus (todo) {
        const todoIndex = this.todos.indexOf(todo)
        this.todos[todoIndex].done = !this.todos[todoIndex].done
      }
    }
  }
</script>

<style scoped>
  .todo-list {
    width: auto;
    background: #ffffff;
    text-align: left;
    padding-bottom: 20px;
    font-family: 'Avenir', Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
  }
</style>
