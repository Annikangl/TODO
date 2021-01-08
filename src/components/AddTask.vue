<template>
  <section class="newtask">
    <button class="btn add__task" @click="modal.show = !modal.show">Добавить задачу</button>
    
    <Modal title="Новая задача" v-show="modal.show" @close="modal.show = false">
      <div slot="body">
        <div class="container newtask__wrapper">
          <div class="form-group">
            <div class="msg-error" v-if="message">{{ message }}</div>
            <label for="task-title" class="task__title-lb">Название</label>
            <input
              type="text"
              id="task-title"
              placeholder="Введите название задачи"
              v-model="title"
              :class="{ 'input-danger': hasError }"
            />
          </div>
          <div class="form-group">
            <select v-model="priority" class="task-priority">
              <option disabled value="">Приоритет</option>
              <option class="normal">Стандартный</option>
              <option class="hight">Важно</option>
              <option class="very=hight">Очень важно</option>
            </select>
          </div>
          <div class="form-group">
            <label for="task-text" class="task__text-lb">Описание</label>
            <textarea
              id="task-text"
              placeholder="Описание задачи"
              v-model="descr"
            ></textarea>
          </div>
          <div class="form-group">
            <button type="button" class="add__task" @click="addTask()">
              Добавить
            </button>
          </div>
        </div>
      </div>
    </Modal>
  </section>
</template>

<script>
import Modal from "./Modal";
export default {
  name: "AddTask",
  components: {
    Modal,
  },
  props: {},

  data() {
    return {
      modal: {
        show: false,
      },
      message: null,
      hasError: false,
      title: "",
      descr: "",
      priority: "",
      note: [],
    };
  },

  methods: {
    addTask() {
      if (this.title == "") {
        this.message = "Поле обязательно";
        this.hasError = true;
        return;
      }
      this.$emit("addTask", {
        title: this.title,
        descr: this.descr,
        date: new Date(Date.now()).toLocaleString(),
        priority: this.priority,
      });
      this.message = null;
      this.title = "";
      this.priority = "";
      this.descr = "";
      this.modal.show = false;
    },
  },
};
</script>

<style></style>
