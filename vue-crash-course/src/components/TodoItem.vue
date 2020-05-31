<template>
    <li>
        <span :class="{done: todo.completed}">
            <input type="checkbox" @click="todo.completed = !todo.completed">
            <strong>{{ index +1 }} </strong>
            {{ todo.title | uppercase}}
        </span>
        <button class="rm"
            @click="$emit('remove-todo',todo.id)"
        >&times;</button>
    </li>
</template>

<script>
    export default {
        name: "TodoItem",
        props: {
            todo:{
                type:Object,
                required: true
            },
            index: Number
        },
        filters:{
            uppercase(value){
                return value.toUpperCase()
            }
        }
    }
</script>

<style scoped>
    li{
        border: 1px solid #cccccc;
        display: flex;
        justify-content: space-between;
        margin-bottom: 1rem;
        padding: .5rem 2rem;
    }
    .rm{
        background-color: red;
        color:#fff;
        border-radius: 50%;
        font-weight: bold;
    }
    input{
        margin-right: 1rem;
    }
    .done{
        text-decoration: line-through;
    }
</style>
