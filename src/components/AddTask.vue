<template>
  <form @submit.prevent>
    <input class="task-input" type="text" v-model="task.text" placeholder="Добавить новую задачу">
    <button class="add-button" @click="addTask">Добавить задачу</button>
  </form>
</template>

<script>
  export default {
    props: {
      text: {
        type: String,
        required: true
      }
    },

    data() {
      return {
        task: {
          text: '',
        }
      }
    },

    methods: {
      addTask() {
        if (this.task.text.length > 0) {
          this.task.id = Date.now();
          this.$emit('add', this.task);
          this.task = {
            text: '',
          }
        }
      },
    }
  }
</script>

<style scoped>
  .task-input {
    padding: 8px;
    font-size: 16px;
    border: 1px solid #ccc;
    border-radius: 5px;
  }

  .add-button {
    padding: 10px;
    background-color: #4caf50;
    color: #fff;
    border: none;
    border-radius: 5px;
    cursor: pointer;
    margin-left: 10px;
  }

  .add-button:hover {
    background-color: #45a049;
  }
</style>