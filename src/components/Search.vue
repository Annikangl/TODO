<template>
    <div class="search__filter">
        <input type="search" id="task-search" placeholder="Поиск" v-model="search">
    </div>
</template>

<script>
export default {
    data() {
        return {
            search: ''
        }
    },

    watch: {
        search(value) {
            this.$emit('search',value);
        }
    }
}
</script>

<style>

</style>