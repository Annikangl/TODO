<template>
<transition name="fade">
  <div class="modal__wrapper" @click="$emit('close')">
      <div class="modal__content" @click.stop="">
          <div class="modal__header">
              <span class="modal-title">{{ title }} </span>
              <span class="task__remove_btn" @click="$emit('close')"></span>
          </div>

          <div class="modal__body">
            <slot name="body"></slot>
          </div>
      </div>
  </div>
</transition>
</template>

<script>
export default {
  name: "Modal",
  props:{
    title: {
      type: String,
      required: true
    }
  },

  data() {
    return {
      
    }
  },

  mounted() {
    document.body.addEventListener('keyup', e => {
      if (e.keyCode === 27) this.$emit('close');
    })
  }

}
</script>

<style lang="scss" scoped>
// Animation
.fade-enter-active, .fade-leave-active {
  transition: opacity .5s;
}
.fade-enter, .fade-leave-to /* .fade-leave-active до версии 2.1.8 */ {
  opacity: 0;
}


.modal__wrapper{
  display: flex;
  justify-content: center;
  align-items: center;
  position: fixed;
  top: 0;
  bottom: 0;
  left: 0;
  transition: opacity .2s ease;
  right: 0;
  z-index: 998;
  background-color: rgba(00,00,00,.78);
}

.modal__content {
  position: relative;
  max-width: 600px;
  padding: 20px 18px;
  background-color: #fff;
  border: 1px solid #dcdfe6;
  transition: all .2s ease;
  border-radius: 8px;
  z-index: 999;
  overflow: hidden;
  @media screen and (min-width: 900px) {
    min-width: 500px;
  }
}
.modal__header {
  display: flex;
  align-self: center;
  justify-content: space-between;
  padding-bottom: 20px;
  span {
    font-size: 24px;
  }
  .btn-close {
    cursor: pointer;
  }
}
.modal__body {
  text-align: center;
}



</style>