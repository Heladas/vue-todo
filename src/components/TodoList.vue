<template>
  <section class="todo-list">
    <div class="counter-block">
      <div>Completed: {{ todos.filter(todo =>{ return todo.done === true}).length }}</div>
      <div>In progress: {{ todos.filter(todo =>{ return todo.done === false}).length }}</div>
    </div>
    <todo v-on:delete-todo="deleteTodo" v-for="todo in todos" v-bind:todo="todo" :key="todo.id"></todo>
  </section>
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
      }
//      addTodo () {
//        console.log('AddTodo')
//      }
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

  .counter-block {
    margin: 0 0 20px 10px;
    font-size: 16px;
    font-weight: bold;
  }
</style>
