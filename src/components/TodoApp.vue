 <template>
    <div class="container">
      <div>
       <div class="imgF img-fluid">
          <h1>TODOs</h1>
         </div>
          <todo-form />
         <todo-list />
       </div>
      
    </div>
 </template>
   
   <script>
import { provide, ref, watchEffect } from 'vue'
import TodoForm from './TodoForm.vue'
import TodoList from './TodoList.vue'
      
   export default {
   components: { TodoForm, TodoList },
   setup() {
      const todos = ref([])
      provide('todos', todos)

      if(localStorage.getItem('todos')){
         todos.value = JSON.parse(localStorage.getItem('todos'))  //porque es un string tengo q convertirlo en un obj
      }

      watchEffect(() => {
         console.log(todos.value.length)
         console.log(todos.value)
         localStorage.setItem('todos', JSON.stringify(todos.value))
      })
   }

}
</script>
   
   <style>
   
         .imgF {
       
           
            background: url('~@/assets/img.png') center center no-repeat;
            background-size: 1200px auto;
         }
      
         h1 {
            padding-block-start: 250px;
            padding-left: 1%;
            
         }
      
   </style>