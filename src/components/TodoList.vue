<template>
  <section class="todo-list">
    <div class="counter-block">
      <div>Completed: {{ todos.filter(todo =>{ return todo.done === true}).length }}</div>
      <div>In progress: {{ todos.filter(todo =>{ return todo.done === false}).length }}</div>
    </div>
    <div class='ui centered card todo-item' v-for="todo in todos" v-bind:style="{background: todo.color}">
      <p class="title">{{todo.title}}</p>
    </div>
  </section>
</template>

<script type="text/javascript">

  export default {
    props: ['todos']
  }
</script>

<style>
  .todo-list{
    width: auto;
    background: wheat;
    margin: 200px auto;
    width: 500px;
    text-align: center;
    padding-bottom: 20px;
    font-family: 'Avenir', Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
  }
  .counter-block{
    margin: 0 0 20px 10px;
    font-size: 16px;
    font-weight: bold;
  }
  .todo-item{
    width: 200px;
    height: 30px;
    margin: 10px 10px;
    /*display: inline-block;*/
    color: white;
    padding: 0 10px;
  }
  .todo-item .title{
    color:white;
    line-height: 30px;
    font-weight: bold;
  }
</style>
