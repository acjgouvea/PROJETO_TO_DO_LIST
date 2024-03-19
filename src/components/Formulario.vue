<template>
    <form @submit.prevent="cadastraTarefa">
        <div class="row">
            <div class="col">
                <input :value="tarefasTemporaria"
                    @change="editaTarefaTemp" required
                    class="form-control" type="text" placeholder="Digite a sua tarefa">
            </div>
            <div class="col-md-2">
                <button type="submit" class="btn btn-primary">Cadastrar</button>
            </div>
            <div class="col-md-2">
                <select @change="trocarFiltro">
                    <option value="todas">Todas tarefas</option>
                    <option value="pendentes">Tarefas pendentes</option>
                    <option value="finalizadas">Tarefas finalizadas</option>
                </select>
            </div>
        </div>
    </form>
</template>

<script>
export default {
    props: ['cadastraTarefa', 'tarefasTemporaria', 'trocarFiltro', 'editaTarefaTemp']
}
</script>
