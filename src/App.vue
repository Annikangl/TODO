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
      tasks: [],
    }
  },

  methods: {
    addTask(task) {
      this.tasks.push(task);
    }
  }
}
</script>

<style>

</style>
