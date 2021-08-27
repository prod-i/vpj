<template>
    <div class="todoList">
        <ul>
            <TodoItem  
                v-for="todo in todos" :key='todo.id'
                v-bind:todo="todo"
                @remove-todo='removeTodo'
                @completed-todo='completedTodo'
            />
        </ul>
    </div>
</template>

<script>
import TodoItem from '@/components/TodoItem'  

export default {
  name: 'TodoList',
  props:['todos'],
  components: {
    TodoItem,
  },
  methods:{
      removeTodo(id){
          this.$emit('remove-todo', id)
      },
      completedTodo(id){
          this.$emit('completed-todo', id)
      }
  }
}
</script>

<style scoped>
    ul {
        list-style: none;
        margin: 40px 0;
        padding: 0;
    }
</style>