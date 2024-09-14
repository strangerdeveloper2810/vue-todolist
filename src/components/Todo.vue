<template>
  <TodoItem
    v-for="todo in todos"
    :key="todo.id"
    :todoProps="todo"
    @mark-item-complete="markItemComplete"
    @delete-todo-item="deleteTodoItem"
  />
</template>

<script>
import { ref } from 'vue'
import TodoItem from './TodoItem.vue'
export default {
  name: 'AppTodo',
  components: {
    TodoItem
  },
  setup() {
    const todos = ref([
      { id: 1, title: 'Todo 1', completed: false },
      { id: 2, title: 'Todo 2', completed: false },
      { id: 3, title: 'Todo 3', completed: false }
    ])
    const markItemComplete = id => {
      todos.value = todos.value.map(todo => {
        if (todo.id === id) {
          todo.completed = !todo.completed
        }
        return todo
      })
    }
    const deleteTodoItem = id => {
      todos.value = todos.value.filter(todo => todo.id !== id)
    }
    return {
      todos,
      markItemComplete,
      deleteTodoItem
    }
  }
}
</script>

<style scoped></style>
