<template>
    <ul class="list-group mt-4">
        <li class="list-group-item" v-for="tarefa in getTarefaFiltrada()" :key="tarefa.titulo">
            <input @change="evento => tarefa.finalizada = evento.target.checked" :id="tarefa.titulo" type="checkbox"
                name="" id="">
            <label :class="{ done: tarefa.finalizada }" class="ms-3" :for="tarefa.titulo">
                {{ tarefa.titulo }}
            </label>
        </li>
    </ul>
</template>