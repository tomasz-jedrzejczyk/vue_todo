<template>
<div class="task" v-bind:class="{ completed: task.completed }">
    <h2>{{ task.title }}</h2>
    <button v-if="!task.completed" @click="removeTask">Zrobione</button>
</div>
</template>

<script>
export default {
    props: ['task'],
    methods: {
        removeTask() {
            this.$emit('remove-clicked', this.task.id)
        }
    }
}
</script>

