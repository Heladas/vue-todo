<template>
  <div id="app">
    <div class="counter-block">
      <div>Completed: {{ todos.filter(todo =>{ return todo.done === true}).length }}</div>
      <div>In progress: {{ todos.filter(todo =>{ return todo.done === false}).length }}</div>
    </div>
    <todo-list v-bind:todos="todos"></todo-list>
    <create-todo v-on:add-todo="addTodo"></create-todo>
  </div>
</template>
<script>

// import Hello from './components/Hello'
import TodoList from './components/TodoList.vue'
import CreateTodo from './components/CreateTodo.vue'

export default {
  name: 'app',
  components: {
    TodoList,
    CreateTodo
  },
  data () {
    return {
      todos: [{
        title: 'Todo A',
        project: 'Project A',
        done: true,
        color: '#3498db'
      }, {
        title: 'Todo B',
        project: 'Project B',
        done: true,
        color: '#41bfb3'
      }, {
        title: 'Todo C',
        project: 'Project C',
        done: false,
        color: '#ffc000'
      }, {
        title: 'Todo D',
        project: 'Project D',
        done: false,
        color: '#f24c3d'
      }, {
        title: 'Todo E',
        project: 'Project E',
        done: false,
        color: '#559977'
      }]
    }
  },
  methods: {
    addTodo (todo) {
      this.todos.push(todo)
    }
  }
}

</script>

<style>
  html, body {
    font-family: 'Avenir', Helvetica, Arial, sans-serif;
    padding: 0;
    margin: 0;
  }

  .clearfix:after {
    content: "."; /* добавить содержимое: "." */
    display: block; /* сделать блоком, т.к. inline не может иметь clear */
    clear: both; /* с обеих сторон clear */
    visibility: hidden; /* сделать невидимым, зачем нам точка внизу? */
    height: 0; /* сделать высоту 0, чтобы не занимал место */
  }

  .noselect {
    -webkit-touch-callout: none; /* iOS Safari */
    -webkit-user-select: none; /* Safari */
    -khtml-user-select: none; /* Konqueror HTML */
    -moz-user-select: none; /* Firefox */
    -ms-user-select: none; /* Internet Explorer/Edge */
    user-select: none; /* Non-prefixed version, currently
                                  supported by Chrome and Opera */
  }

  .counter-block {
    margin: 0 0 20px 10px;
    font-size: 16px;
    font-weight: bold;
  }

  .todo-list, .create-todo {
    float: left;
  }
</style>
