<template>

    <li class="list-group-item d-flex justify-content-between align-items-center">
        <span role="button" @click="completado(todo.id)" :class="{'tachado': todo.estado}">
            {{ todo.texto }}
        </span>
        <span role="button" @click="eliminar(todo.id)">
            <i class="fa-solid fa-xmark"></i>
        </span>
    </li>


</template>

<script>
import { inject } from 'vue';

export default {
    props: {
        todo:{
            type: Object,
            require: true
        }
    },
    setup(){
        const todos = inject('todos')
        const eliminar = id =>{
            todos.value = todos.value.filter(item => item.id !== id)
        }
        const completado = id =>{
            todos.value = todos.value.map(item => {
                if(item.id === id){
                    item.estado = true
                }
                return item
            })
        }
        return {eliminar, completado}
    }
}
</script>

<style>
.tachado{
    text-decoration: line-through;
}
</style>