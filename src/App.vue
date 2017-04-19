<template>
  <div id="app">
    <todo-list v-bind:todos="todos"></todo-list>
  </div>
</template>

<script>

// import Hello from './components/Hello'
import TodoList from './components/TodoList.vue'

export default {
  name: 'app',
  components: {
    TodoList
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
  }
}

</script>

<style>
  html,body{
    padding: 0;
    margin: 0;
  }
/*#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}*/
</style>
