<template>
<div>

  <div class="task">
    <p>Nowe zadanie: {{ newTask }}</p>
    <input type="text" placeholder="Wprowadz zadanie" v-model="newTask">
    <button @click="addTask">Dodaj</button>
  </div>

  <ToDoTask 
    v-for="task in tasks" 
    :key="task.id"
    :item="task"
    @remove-clicked="removeTask"
  />

</div>
</template>

<script>
import ToDoTask from './ToDoTask.vue'

  export default {
    components: {
      ToDoTask
    },
    data() {
      return {
        newTask: '',
        tasks: [
          { title: 'Umyć samochód', completed: false, id: 1 },
          { title: 'Wyprowadzić psa', completed: false, id: 2 }
        ]
      }
    },
    methods: {
      addTask() {
        this.tasks.push({
          title: this.newTask, 
          completed: false, 
          id: Math.random 
        })
        this.newTask = ''
      },
      removeTask(id) {
        const index = this.tasks.findIndex(el => el.id === id)
        this.tasks[index].completed = true
      }
    }
  }
</script>

<style>
  .task {
    border: 1px solid #cdcdcd;
    margin: 8px;
    padding: 10px;
  }
  .completed {
    opacity: 0.5;
  }
  .completed h2 {
    text-decoration: line-through;
  }
</style>
