<template>
  <div id="id">
    <AppHeader />
    <AppTodo />
  </div>
</template>

<script>
import AppHeader from './components/Header.vue'
import AppTodo from './components/Todo.vue'
export default {
  name: 'App',
  components: {
    AppHeader,
    AppTodo
  }
}
</script>

<style>
#add {
  font-family: Avenir, Helvetica, Arial, sans-serif;
}
</style>
