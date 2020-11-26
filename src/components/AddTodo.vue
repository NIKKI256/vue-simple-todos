<template>
    <form @submit.prevent="addTodo">
        <input type="text" placeholder="title" v-model="title">
        <button type="submit">Create</button>
    </form>
</template>

<script>
export default {
    data(){
        return{
            title:''
        }
    },
    methods:{
        addTodo(){
            if(this.title){
                var newTodo = {
                    title:this.title,
                    id:Date.now(),
                    completed:false
                }

                this.$emit('add-todo',newTodo)
                
                this.title=''
            }
        }
    }
}
</script>

<style scoped>
    input{
            width: 400px;
        }
</style>