<template>
  <div id="app">
    <!-- <HelloWorld msg="Bhargav Koritala"/> -->
    <header>
            <h1>Todo-List</h1>
    </header>
    <AddTask v-on:addTask="addNew"/>
    <Todos  v-bind:list="items" v-on:del-todo="deleteThis"/>
    
  </div>
</template>

<script>
//import HelloWorld from './components/HelloWorld.vue'
import Todos from '../components/Todos.vue';
import AddTask from '../components/AddTask';
import axios from 'axios';

export default {
  name: 'home',
  components: {
    Todos,
    AddTask
  },
  data(){
    return {
      items:[]
    }
  },
  methods:{
    deleteThis(id){
      axios.delete(`https://jsonplaceholder.typicode.com/todos/${id}`)
      .then(() => this.items = this.items.filter((item)=>item.id!=id))
      .catch(err=>console.log(err))
      //this.items = this.items.filter((item)=>item.id!=id)
    },
    addNew(newTask){
      axios.post('https://jsonplaceholder.typicode.com/todos',{
        title : newTask.title,
        completed : newTask.completed
      })
      .then(response => {
        console.log(response.data);
        this.items = [...this.items,response.data];
      })
      
    }
  },
  created(){
    axios.get('https://jsonplaceholder.typicode.com/todos?_limit=5')
    .then(response=> this.items = response.data)
    .catch(err=>console.log(err))
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
