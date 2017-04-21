<template>
  <div class='ui centered card todo-item' v-bind:style="{background: todo.color}">
    <div class="info">
      <p class="title">{{todo.title}}</p>
      <p class="project">{{todo.project}}</p>
    </div>

    <div class="delete" v-on:click="deleteTodo(todo)">Delete</div>
    <div class="edit" v-on:click="toggleForm">Edit</div>
    <div class='status'>{{ getStatus }}</div>

    <div class="content" v-show="isEditing">
      <div class='form'>
        <div class='field'>
          <label>Title</label>
          <input type='text' v-model="todo.title">
        </div>
        <div class='field'>
          <label>Project</label>
          <input type='text' v-model="todo.project">
        </div>
      </div>
    </div>

  </div>
</template>

<script>

  export default {
    props: ['todo'],
    data () {
      return {
        isEditing: false
      }
    },
    computed: {
      getStatus: function () {
        let status = (this.todo.done ? 'Completed' : 'Pending')
        return status
      }
    },
    methods: {
      toggleForm () {
        this.isEditing = !this.isEditing
      },
      deleteTodo (todo) {
        this.$emit('delete-todo', todo)
      }
    }
  }

</script>

<style scoped>
  .todo-item {
    width: 350px;
    /*height: 30px;*/
    margin: 10px 10px;
    color: black;
    padding: 0 10px;
  }

  .todo-item .title, .todo-item .project {
    /*line-height: 30px;*/
    font-size: 14px;
    font-weight: bold;
    display: inline-block;
    width: 100%;
    margin: 10px auto 0;
  }

  .todo-item .status, .todo-item .edit,.todo-item .delete{
    font-size: 14px;
    font-weight: bold;
    display: block;
    float: right;
    margin: 10px 5px 0;
  }

  .todo-item .edit:hover, .todo-item .delete:hover {
    text-decoration: underline;
    cursor: pointer;
  }
  .info{
    height: 60px;
    width: 150px;
    display: inline-block;
  }
  .form label{
    display: inline-block;
    width: 50px;
  }
  .form input{
    margin: 10px 10px 5px;
    display: inline-block;
  }
</style>
