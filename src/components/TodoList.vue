<template>
    <div>
        <TodoItem
        v-for="(todo,index) in todos" :key="todo.id"
        v-bind:todo="todo"
        v-bind:index="index"
        @remove-todo="RemoveTodo"
        />
    </div>
</template>

<script>
import TodoItem from '@/components/TodoItem'

export default {
    props:{
        todos:{
            type:Array
        }
    },
    components:{
        TodoItem
    },
    methods:{
        RemoveTodo(id){
            this.$emit('remove-todo',id)
        }
    }
}
</script>