<template>
    <div class="item">
        <span :class="{done: todo.completed}">
            <input type="checkbox" @change="todo.completed=!todo.completed">
            <b>{{index + 1}}</b>
            {{todo.title}}
        </span>
            <button class="rm" @click="$emit('remove-todo',todo.id)">&times;</button>
    </div>
</template>

<script>
export default {
    props:{
        todo:{
            type:Object
        },
        index:Number
    }
}
</script>

<style >
    .item{
        border: 1px solid #ccc;
        display: flex;
        justify-content: space-between;
        padding: .5rem 2rem;
        margin: auto;
        margin-bottom: 1rem;
        width: 70%;
    }

    span{
        font-size: 1em;
    }

    .done{
        text-decoration: line-through;
    }

    .rm{
        background: red;
        color: #fff;
        border-radius: 50%;
        font-weight: bold;
        outline: none;
    }
</style>