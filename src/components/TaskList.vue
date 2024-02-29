<template>
  <div class="content">
    <h2>Список задач <span v-if="tasks.length <= 0">пуст</span></h2>
    <ul class="task-list" v-if="tasks.length > 0">
      <li class="task-item" v-for="(task, index) in tasks" :key="task.id">
        <span><b>{{ task.text }}</b></span>
        <button @click="deleteTask(index)" class="delete-button">Удалить</button>
      </li>
    </ul>
  </div>
</template>

<script>
  export default {
    props: {
      tasks: {
        type: Array,
        required: true
      }
    },

    methods: {
      deleteTask(index) {
        this.tasks.splice(index, 1);
      }
    }
  }
</script>

<style>
  .content {
    margin-top: 20px;
    text-align: center;
  }

  .task-list {
    margin-top: 10px;
    list-style-type: none;
    padding: 0;
  }

  .task-item {
    display: flex;
    align-items: center;
    margin-bottom: 10px;
  }

  .delete-button {
    margin-left: 10px;
    padding: 5px 10px;
    background-color: #ff5c5c;
    color: #fff;
    border: none;
    border-radius: 5px;
    cursor: pointer;
  }

  .delete-button:hover {
    background-color: #ff3b3b;
  }
</style>