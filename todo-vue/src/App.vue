<script setup>
import { reactive } from 'vue';

const estadoTarefa = reactive({
  filter: 'todas',
  tarefasTemporaria: '' ,
  tarefas: [
    {
      titulo: 'Estudar Java',
      finalizada: false,
    },
    {
      titulo: 'Estudar SASS',
      finalizada: true
    },
    {
      titulo: 'Treinar',
      finalizada: true
    }
  ]
})

const getTarefaPendente = () => {
  return estadoTarefa.tarefas.filter(tarefa => !tarefa.finalizada).length
}
const getTarefafinalizada = () => {
  return estadoTarefa.tarefas.filter(tarefa => tarefa.finalizada).length
}

const getTarefaFiltrada = () => {
  const { filter } = estadoTarefa;

  switch (filter) {
    case 'pendentes':
      return estadoTarefa.tarefas.filter(tarefa => !tarefa.finalizada);
    case 'finalizadas':
      return estadoTarefa.tarefas.filter(tarefa => tarefa.finalizada);
    default:
      return estadoTarefa.tarefas;
  }
}
const cadastraTarefa = () => {

const tarefaNova ={
  titulo: estadoTarefa.tarefasTemporaria,
  finalizada: false,
}
estadoTarefa.tarefas.push(tarefaNova);
estadoTarefa.tarefasTemporaria = '';

}
</script>

<template>
  <div class="container">
    <header class="p-5 mb-4 mt-4 bg-light rounded-3">
      <h1>Minhas tarefas</h1>
      <p>
        Você possui {{ getTarefaPendente() }} tarefas pendentes
      </p>
    </header>
    <form @submit.prevent="cadastraTarefa">
      <div class="row">
        <div class="col">
          <input :value="estadoTarefa.tarefasTemporaria" @change="evento => estadoTarefa.tarefasTemporaria = evento.target.value" required class="form-control" type="text" placeholder="Digite a sua tarefa">
        </div>
        <div class="col-md-2">
          <button type="submit" class="btn btn-primary">Cadastrar</button>
        </div>
        <div class="col-md-2">
          <select @change="evento => estadoTarefa.filter = evento.target.value" class="form-control">
            <option value="todas">Todas tarefas</option>
            <option value="pendentes">Tarefas pendentes</option>
            <option value="finalizadas">Tarefas finalizadas</option>
          </select>
        </div>
      </div>
    </form>

    <ul class="list-group mt-4">
      <li class="list-group-item" v-for="tarefa in getTarefaFiltrada()" :key="tarefa.titulo">
        <input @change="evento => tarefa.finalizada = evento.target.checked"  :id="tarefa.titulo" type="checkbox" name="" id="">
        <label :class="{ done: tarefa.finalizada }" class="ms-3" :for="tarefa.titulo">
          {{ tarefa.titulo }}
        </label>
      </li>
    </ul>
  </div>
</template>

<style scoped>
.done {
  text-decoration: line-through;
}
</style>
