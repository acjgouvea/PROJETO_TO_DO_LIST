<script setup>
import { reactive } from 'vue';
import Cabecalho from './components/Cabecalho.vue';
import Formulario from './components/Formulario.vue';
import Lista from './components/Lista.vue';

const estadoTarefa = reactive({
  filter: 'todas',
  tarefasTemporaria: '',
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

  const tarefaNova = {
    titulo: estadoTarefa.tarefasTemporaria,
    finalizada: false,
  }
  estadoTarefa.tarefas.push(tarefaNova);
  estadoTarefa.tarefasTemporaria = '';

}
</script>

<template>
  <div class="container">
    <Cabecalho :tarefas-pendentes="getTarefaPendente().length" />
    <Formulario />
    <Lista />

  </div>
</template>

<style scoped>
.done {
  text-decoration: line-through;
}
</style>
