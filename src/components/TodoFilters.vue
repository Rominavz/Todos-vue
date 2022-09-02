<template>
    <div class="card mt-3 ">
        <div class="card-body d-flex justify-content-between align-items-center">
            <spanf role="button" @click="filtrar('active')">
                Actives
            </spanf>
            <spanf role="button" @click="filtrar('all')">
                All
            </spanf>
            <spanf role="button" @click="filtrar('complete')">
                Completed
            </spanf>
        </div>
    </div>
</template>

<script>
import { inject } from 'vue'
export default {
    setup() {
        const estado = inject('estado')
      
        const filtrar = valor =>{
            estado.value = valor
        }
        return {filtrar}
    },
}
</script>

<style>
spanf{
   font-weight: bold;
}
</style>