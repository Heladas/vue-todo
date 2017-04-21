<template>
  <div class="create-todo">
    <div class="add-todo-btn" v-on:click="openForm" v-show="!isCreating">Add todo</div>

    <div class="add-form" v-show="isCreating">
      <div>
        <label>Title:</label>
        <input type="text" v-model="titleText" defaultValue="">
      </div>
      <div>
        <label>Project:</label>
        <input type="text" v-model="projectText" defaultValue="">
      </div>
      <div>
        <label>Color:</label>
        <input type="text" v-model="color">
      </div>
      <div class="create" v-on:click="sendForm()">Create</div>
      <div class="close" v-on:click="closeForm()">Close</div>
    </div>
  </div>
</template>

<script>

  export default {
    data () {
      return {
        titleText: '',
        projectText: '',
        color: '',
        isCreating: false
      }
    },
    methods: {
      openForm () {
        this.isCreating = true
      },
      closeForm () {
        this.isCreating = false
      },
      sendForm () {
        if (this.titleText.length > 0 && this.projectText.length > 0) {
          const title = this.titleText
          const project = this.projectText
          const color = this.color
          this.$emit('add-todo', {
            title,
            project,
            color,
            done: false
          })
        }
        this.isCreating = false
        this.titleText = ''
        this.color = ''
        this.projectText = ''
      }
    }
  }

</script>
<style scoped>
  .add-todo-btn {
    display: inline-block;
    margin: 10px 10px;
    font-weight: bold;
    cursor: pointer;
  }

  .add-todo-btn:hover {
    text-decoration: underline;
  }

  .add-form{
    width: 350px;
    /* height: 30px; */
    margin: 10px 10px;
    padding: 0 10px;
    background-color: darkseagreen;
  }

  label{
    display: inline-block;
    width: 100px;
  }
  input{
    margin-top: 10px;
  }
  .add-form .create, .add-form .close {

    margin-top: 10px;
    font-weight: bold;
    cursor: pointer;
  }
  .add-form .create:hover, .add-form .close:hover {
    text-decoration: underline;
  }
</style>
