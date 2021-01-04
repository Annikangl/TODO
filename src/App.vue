<template>
  <div class="wrapper">
    <div class="wrapper-content">
      <todoHeader></todoHeader>
      <addTask @addTask='addTask($event)'></addTask>
      <tasks :tasks ="tasks"></tasks>
    </div>
  </div>
</template>

<script>
import todoHeader from '@/components/Header';
import addTask from '@/components/AddTask';
import tasks from '@/components/Tasks';

export default {
  name: 'App',
  components: {
    todoHeader,
    addTask,
    tasks
  },
  data() {
    return {
      tasks: JSON.parse(localStorage.getItem('tasks')) ? JSON.parse(localStorage.getItem('tasks')): [],
    }
  },

  methods: {
    addTask(task) {
      let tasks = this.tasks;
      tasks.push(task);
      localStorage.setItem('tasks',JSON.stringify(tasks)); // добавляем заметку в LocalStorange
    },

  }
}
</script>

<style>

</style>
