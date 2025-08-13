<script setup>
const props = defineProps(['tarefas', 'filtro']);
</script>

<template>
    <ul v-if="props.tarefas.length > 0" class="list-group mt-4">
        <li class="list-group-item" v-for="tarefa in props.tarefas">
            <input @change="evento => tarefa.finalizada = evento.target.checked" :checked="tarefa.finalizada"
                :id="tarefa.titulo" type="checkbox">
            <label :class="{ done: tarefa.finalizada }" class="ms-3" :for="tarefa.titulo">
                {{ tarefa.titulo }}
            </label>
        </li>
    </ul>
    <p class="mt-5 aviso" v-else>
        {{ props.filtro === 'Finalizadas' ? 'Nenhuma tarefa finalizada!'
            : props.filtro === 'Pendentes' ? 'Nenhuma tarefa pendente!'
                : 'Nenhuma tarefa!'
        }}

    </p>
</template>

<style scoped>
.done {
    text-decoration: line-through;
}

.aviso {
    color: #fff;
    border-radius: 6px;
    border: none;
    background-color: red;
    font-weight: bold;
    padding: 8px;
    text-align: center;
}
</style>