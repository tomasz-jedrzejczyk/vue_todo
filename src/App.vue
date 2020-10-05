<template>
  <div>
    <h1>Todo App</h1>
    <ToDoApp />
  </div>
</template>

<script>
import ToDo from './components/ToDoApp.vue'

export default {
     components: {
    ToDoApp: ToDo
  }
}
</script>