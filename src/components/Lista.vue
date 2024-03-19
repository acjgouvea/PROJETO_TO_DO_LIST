<template>
    <ul class="list-group mt-4">
        <li class="list-group-item" v-for="tarefa in props.tarefas" :key="tarefa.titulo">
            <input v-model="tarefa.finalizada" :id="tarefa.titulo" type="checkbox" class="form-check-input">
            <label :for="tarefa.titulo" class="form-check-label" :class="{ 'done': tarefa.finalizada }">
                {{ tarefa.titulo }}
            </label>
        </li>
    </ul>
</template>

<script setup>
const props = defineProps(['tarefas']);
</script>

<style scoped>
.done {
    text-decoration: line-through;
}
</style>
