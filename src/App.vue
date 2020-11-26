<template>
  <div id="app">
    <h1>Todo application</h1>
    <AddTodo
    @add-todo="addTodo"
    />
    <hr>
    <select v-model="filter">
      <option value="all">All</option>
      <option value="completed">Completed</option>
      <option value="not-completed">Not completed</option>
    </select>
    <hr>
    <Loader v-if="loading"/>
    <TodoList
    v-else-if="filteredTodos.length"
    v-bind:todos="filteredTodos"
    @remove-todo="RemoveTodo"
    />
    <h1 v-else>No todos!</h1>
  </div>
</template>

<script>
import TodoList from '@/components/TodoList'
import AddTodo from '@/components/AddTodo'
import Loader from '@/components/Loader'

export default {
  name: 'App',
  data(){
    return{
      todos:[
        {id:1,title:'Дело №1',completed:false},
        {id:2,title:'Дело №2',completed:false},
        {id:3,title:'Дело №3',completed:false},
      ],
      filter:'all',
      loading:false
    }
  },
  components: {
    TodoList,AddTodo,Loader
  },
  methods:{
    RemoveTodo(id){
      this.todos = this.todos.filter(t => t.id != id)
    },
    addTodo(todo){
      this.todos.push(todo)
    }
  },
  computed:{
    filteredTodos(){ 
        this.loading=true

        setTimeout(() => {this.loading=false}, 1000);
        
        if(this.filter === 'all'){
          return this.todos
        }

        if(this.filter === 'completed'){
          return this.todos.filter(t => t.completed)
        }

        if(this.filter === 'not-completed'){
          return this.todos.filter(t => !t.completed)
        }    
    }
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
  width: 85%;
  margin: auto;
  margin-top: 60px;
}

select{
  width: 200px;
}
</style>
