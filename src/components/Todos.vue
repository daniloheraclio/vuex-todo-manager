<template>
  <div>
    <h3>Todos component</h3>
  <div class="todos">
    <div v-for="todo in allTodos" :key="todo.id" class="todo">
      {{ todo.title }}
      <i @click="deleteTodo(todo.id)" class="fi-xnsuxl-trash-bin"></i>  
    </div>
    
  </div>
  </div>
</template>

<script>
import { mapGetters, mapActions } from 'vuex';
export default {
   name: "Todos",
   methods: {
     ...mapActions(['fetchTodos', 'deleteTodo'])
   },
   computed: mapGetters(['allTodos']),
   created() {
     this.fetchTodos();
   }
}
</script>

<style scoped>

.todos {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  grid-gap: 1rem
}

.todo {
  border: 1px sokid #ccc;
  background: #41b883;
  padding: 1rem;
  border-radius: 5px;
  text-align: center;
  position: relative;
  cursor: pointer;
}

i {
  position: absolute;
  bottom: 10px;
  right: 10px;
  color: #fff;
  cursor: pointer;
}

</style>