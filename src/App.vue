<template>
  <div class="container">
    <AddTask :text="text" @add="addTask"></AddTask>
    <TaskList :tasks="tasks"></TaskList>
  </div>
</template>

<script>
  import AddTask from '@/components/AddTask.vue'
  import TaskList from '@/components/TaskList.vue'

  export default {
    components: {
      AddTask,
      TaskList
    },

    data() {
      return {
        tasks: [
          { id: 1, text: 'Learn Vue.js 3' },
        ],
        text: ''
      }
    },

    methods: {
      addTask(task) {
        this.tasks.push(task);
      },
    }
  }
</script>
  
<style>
  * {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
  }

  .container {
    display: flex;
    flex-direction: column;
    align-items: center;
    padding: 20px;
  }
</style>
