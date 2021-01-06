<template>
  <header class="header">
      <div class="container">
          <div class="header__inner">
              <h1 class="header__title">{{ title }} </h1>
              <div class="header__app__mode">
                  <label for="dark__mode" class="dark__mode-label">{{ themeSwitcher }}</label>
                  <input type="checkbox" id="dark__mode-checkbox" v-model="themeSwitcher" :true-value="on" :false-value="off" @change="switchTheme()">
              </div>
          </div>
      </div>
  </header>
</template>

<script>
export default {
    name: 'Header',
    props: {},

    data() {
        return {
            title: "My TODO",
            themeSwitcher: 'Dark',
            on: 'Light',
            off: "Dark",
        }
    },

    methods: {
        switchTheme() {
            this.$emit('switchTheme',this.themeSwitcher);
        }
    }
}
</script>

<style>

</style>