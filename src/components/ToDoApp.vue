<template>
<div>

  <div class="task">
    <p>Nowe zadanie: {{ newTask }}</p>
    
    <input 
      type="text" 
      placeholder="Wprowadz zadanie" 
      v-model="newTask"
    >
    <button 
     @click="addTask"
    >Dodaj</button>
  </div>

  <div 
  class="task" 
  v-bind:class="{
    completed: task.completed
  }"
  v-for="task in tasks" 
  v-bind:key="task.id"
  >
    <h2>{{ task.title }}</h2>
    <button v-if="!task.completed" @click="removeItem(task.id)">Zrobione</button>
  </div>
</div>
</template>

<script>
  export default {
    data() {
      return {
        newTask: '',
        tasks: [
          { title: 'Umyć samochód', completed: true, id: 1 },
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
      removeItem(id) {
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
