<template>
    <form @submit.prevent="cadastraTarefa">
        <div class="row">
            <div class="col">
                <input :value="estadoTarefa.tarefasTemporaria"
                    @change="evento => estadoTarefa.tarefasTemporaria = evento.target.value" required
                    class="form-control" type="text" placeholder="Digite a sua tarefa">
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




</template>