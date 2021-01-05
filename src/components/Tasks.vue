<template>
  <section class="tasks">
      <div class="container">
          <div class="tasks__filters">
              <search @search='search = $event'></search>
              <div class="column__filter">
                  <img src="../assets/img/svg/row.svg" alt="row" class="column__img" :class="{ active: isActive }" @click="isActive = true" >
              </div>
              <div class="grid__filter">
                  <img src="../assets/img/svg/grid.svg" alt="grid" class="grid__img" :class="{ active: !isActive }" @click="isActive = false" >
              </div>
          </div>
          <div v-if="!tasks.length" class="notif">
              <p class="notif-empty">Заметок нет</p>
              <img src="../assets/img/sad_emj.png" alt="sad" class="notif-empty__img">
          </div>
          <div class="tasks-wrapper"  v-else>
          <div class="task" :class="{ grid: !isActive}"  v-for="(task,index) in tasksFilter" :key="index">
              <div class="task__header">
                  <div class="task__created__date">{{ task.date }}</div>
                  <div class="task__actions">
                      <button class="task__edit_btn" type="button"></button>
                      <button class="task__remove_btn" type="button" @click="removeTask(index)"></button>
                  </div>
              </div>
              <div class="task__content">
                  <div class="content__title"> {{ task.title}} </div>
                  <div class="content__text">
                      {{ task.descr }}
                    </div>
              </div>
          </div>
        </div>
      </div>
  </section>
</template>

<script>


import search from './Search';
export default {
    components: {
        search
    },

    props: {
        tasks: {
            type: Array
        }
    },

    data() {
        return {
            isActive: true,
            search: ''
        }
    },

    computed: {
        tasksFilter() {
            let arr = this.tasks;
            let search = this.search;

            if (!search) return arr;

            search = search.trim().toLowerCase();
            arr = arr.filter(function(item) {
                if (item.title.toLowerCase().indexOf(search) !== -1) {
                return item;
                }
            })
            return arr;
        }
    },

    methods: {
        // сделать по нормальному
        removeTask(id) {
            this.tasks.splice(id,1);
            let currentTasks = JSON.parse(localStorage.tasks);
            currentTasks.splice(id,1);
            localStorage.setItem('tasks', JSON.stringify(currentTasks));
        },
    }
}
</script>

<style>

</style>