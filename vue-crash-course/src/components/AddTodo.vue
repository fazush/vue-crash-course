<template>
    <form @submit.prevent="onsubmit">
        <input type="text" v-model="title">
        <button type="submit">Create</button>
    </form>
</template>

<script>
    export default {
        name: "AddTodo",
        data(){
            return{
                title:''
            }
        },
        methods:{
            onsubmit(){
                if (this.title.trim()){
                    const newTodo = {
                        id: Date.now(),
                        title:this.title,
                        completed: false
                    }
                    this.$emit('add-todo', newTodo)
                    this.title = ''
                }
            }
        }
    }
</script>

<style scoped>
    form{
        display: flex;
    }
    input{
        width: 100%;
        margin-right: 5px;
    }
</style>
