<template>
        <li>
            <span v-bind:class='{done: todo.completed}'>
                <input type="checkbox" v-on:change="$emit('completed-todo', todo.id)">
                <strong class="title">{{todo.title}}</strong>
            </span>
            <button v-on:click="$emit('remove-todo', todo.id)">&times;</button>
        </li>
</template>

<script>

export default {
  name: 'TodoItem',
  props:{
      todo:{
          type: Object,
          required: true,
      }
  },
  components: {}
}
</script>

<style scoped>
    li{
        /* border: 1px solid #ccc; */
        max-width: 600px;
        width: 90%;
        box-shadow: 0px 2px 10px rgba(0, 0, 0, 0.1);
        display: flex;
        justify-content: space-between;
        padding: 10px 20px;
        margin: 20px auto;
    }
    .title{
        margin-left: 15px;
    }
    button{
        font-size: 14px;
        border-radius: 100%;
        border: none;
        background-color: #af4646;
        width: 20px;
        height: 20px;
        color: #fff;
    }
    .done{
        text-decoration: line-through;
        color: #ccc;
    }
</style>