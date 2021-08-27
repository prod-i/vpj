<template>
  <div class="app">

    <h1>Todo List</h1>

    <AddTodo @add-todo='addTodo'/>

    <hr>

    <TodoList 
      v-bind:todos="todos"
      @remove-todo="removeTodo"
      @completed-todo="completedTodo"
    />

  </div>
</template>

<script>
import TodoList from '@/components/TodoList'  
import AddTodo from '@/components/AddTodo'  

export default {
  name: 'App',

  data(){
    return {
      todos: [
        {id:1, title:'Приготовить завтрак', completed:false},
        {id:2, title:'Приготовить обед',    completed:false},
        {id:3, title:'Приготовить полдник', completed:false},
        {id:4, title:'Приготовить ужин',    completed:false},
      ],
    }
  },

  mounted(){
    fetch('https://jsonplaceholder.typicode.com/todos?_limit=5') 
    .then(response => response.json()) 
    .then(json => {
      this.todos = json
    })
  },

  methods:{
    removeTodo(id){
      this.todos = this.todos.filter(t => t.id !== id)
    },
    completedTodo(id){
      this.todos[id-1].completed = !this.todos[id-1].completed
    },
    addTodo(item){
      this.todos.unshift(item)
    }
  },

  components: {
    TodoList,
    AddTodo,
  }

}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
