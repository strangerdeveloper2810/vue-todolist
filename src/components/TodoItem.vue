<template>
  <p :class="['todo-item', todoProps.completed ? 'is-complete' : '']">
    <input type="checkbox" :checked="todoProps.completed" @change="markItemComplete" />
    {{ todoProps.title }}
    <button class="btn-delete" @click="handleDeleteItem">Delete</button>
  </p>
</template>

<script>
export default {
  name: 'TodoItem',
  props: ['todoProps'],
  setup(props, context) {
    const markItemComplete = () => {
      context.emit('mark-item-complete', props.todoProps.id)
    }
    const handleDeleteItem = () => {
      context.emit('delete-todo-item', props.todoProps.id)
    }
    return {
      markItemComplete,
      handleDeleteItem
    }
  }
}
</script>

<style scoped>
.todo-item {
  background: #f4f4f4;
  padding: 10px;
  margin: 0;
  border-bottom: 1px dotted #ccc;
}
.is-complete {
  text-decoration: line-through;
}
.btn-delete {
  background-color: red;
  color: white;
  border: none;
  padding: 5px 10px;
  border-radius: 5px;
  cursor: pointer;
  float: right;
}
</style>
