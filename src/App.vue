<template>
  <div class="wrapper" :class="{ dark: darkMode }">
    <div class="wrapper-content">
      <todoHeader :class="{ dark: darkMode }" @switchTheme=switchTheme($event)></todoHeader>
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
      darkMode: false,
    }
  },


  methods: {
    addTask(task) {
      let tasks = this.tasks;
      tasks.push(task);
      localStorage.setItem('tasks',JSON.stringify(tasks)); // добавляем заметку в LocalStorange
    },

    switchTheme(value) {
      value == 'Light' ? this.darkMode = true : this.darkMode = false;
      // return this.darkMode;
    }
  },

  watch: {
    darkMode() {
      localStorage.setItem('darkMode',JSON.stringify(this.darkMode));
    }
  },

  created() {
    this.darkMode = JSON.parse(localStorage.getItem('darkMode'));
  }
}
</script>

<style>

</style>
