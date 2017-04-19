<template>
  <div class='ui centered card todo-item' v-bind:style="{background: todo.color}">
    <p class="title">{{todo.title}}</p>
    <div class='status' v-show="todo.done">
      Completed
    </div>
    <div class='status' v-show="!todo.done"></div>
  </div>
</template>

<script>

  export default {
    props: ['todo']
  }

</script>

<style scoped>
  .todo-item {
    width: 250px;
    height: 30px;
    margin: 10px 10px;
    cursor: pointer;
    color: white;
    padding: 0 10px;
  }

  .todo-item .title {
    color: white;
    line-height: 30px;
    font-weight: bold;
  }

  .todo-item .status {
    font-size: 14px;
    font-weight: bold;
    color: white;
    display: block;
    float: right;
    line-height: 30px;
  }
</style>
