<template>
  <header class="header">
      <div class="container">
          <div class="header__inner">
              <h1 class="header__title">{{ title }} </h1>
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