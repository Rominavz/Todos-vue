<template>
     <li class="list-group-item d-flex justify-content-between align-items-center">
        <span role="button">
            {{contarActivos}} Actives
        </span>
        <span role="button" @click="eliminarCompletados">
            Delete completed
        </span>
       
    </li>
</template>

<script>
import { computed, inject } from 'vue';

export default {
    setup() {
        const todos = inject('todos')
        const contarActivos = computed(()=>{
            return todos.value.filter(item => item.estado === false).length
        })
        const eliminarCompletados = () =>{
            todos.value = todos.value.filter(item => item.estado === false)
        }
            return {contarActivos, eliminarCompletados}
    },
}
</script>

<style>

</style>