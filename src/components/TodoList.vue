<template>
    <ul class="list-group">
        <todo-item v-for="todo in todos" :key="todo.id" :todo="todo" />
        <li v-if="todos.length === 0" class="list-group-item">
            No hay Todos
        </li>
        <todo-footer v-if="todos.length !== 0" />
        <todo-filters/>
    </ul>
</template>

<script>
import { inject, ref, computed, provide } from 'vue'
import TodoItem from './TodoItem.vue'
import TodoFooter from './TodoFooter.vue'
import TodoFilters from './TodoFilters.vue'


export default {
    components: { TodoItem, TodoFooter, TodoFilters },
    setup() {
        const todosAll = inject('todos')
        const estado = ref('all')
        const todos = computed(() =>{
            if(estado.value === 'all'){
                return todosAll.value
            }
            if(estado.value === 'active'){
                return todosAll.value.filter(item => item.estado === false)
            }
            if(estado.value === 'complete'){
                return todosAll.value.filter(item => item.estado === true)
            }
        })
        provide('estado', estado) //lo pongo a disposicion para poder pasarlo al comp todoFilters
        return {todos}
        },
}
</script>

<style>

</style>