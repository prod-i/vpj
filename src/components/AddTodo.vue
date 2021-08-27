<template>
    <form @submit.prevent='onSubmit'>
        <input type="text" v-model='title'>
        <button type="submit">Create</button>
    </form>
</template>

<script>
export default {
    data(){
        return {
            title: '',
        }
    },
    methods: {
        onSubmit(){
            if(this.title.trim()){
                const newTodo = {
                    id: Date.now(),
                    title: this.title,
                    completed: false,
                }
               this.$emit('add-todo', newTodo);
               this.title = ''; 
            }
        }
    }
}
</script>

<style scoped>
    form{
        display: flex;
        justify-content: space-between;
        max-width: 600px;
        width: 95%;
        margin: 40px auto 25px auto;
    }
    input{
        width: 80%;
        height: 30px;
        outline: none;
        border: 1px solid #ccc;
        padding-left: 5px;
        box-shadow: 0px 2px 10px rgba(0, 0, 0, 0.2 );
    }
    button{
        width: 18%;
        border: none;
        background-color: #af4646;
        color: #fff;
    }
</style>