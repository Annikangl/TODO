<template>
  <header class="header">
      <div class="container">
          <div class="header__inner">
              <h1 class="header__title">{{ title }} </h1>
              <div class="header__app__mode">
                  <label for="dark__mode" class="dark__mode-label">Dark</label>
                  <input type="checkbox" id="dark__mode-checkbox">
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
            title: "My TODO"
        }
    }
}
</script>

<style>

</style>