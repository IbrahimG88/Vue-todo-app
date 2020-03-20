<template>
  <div id="app">
    <Header />
    <!-- v-on: on event we call it add-todo, that call addTodo(), the event I think is using the AddTodo component-->
    <AddTodo v-on:add-todo="addTodo" />
    <!-- receives the emitted todo.id from del-todo sent by the v-on from Todos.vue, deleteTodo function can now receive the todo.id
    as an argument as it was paased from Todos component up to here in App.vue component-->
    <Todos v-bind:todos = "todos" v-on:del-todo="deleteTodo"/>
    
  </div>
</template>

<script>
import Todos from './components/Todos';
import Header from './components/Layout/Header';
import AddTodo from './components/AddTodo';
import axios from 'axios';

export default {
  name: 'App',
  components: {
    Todos,
    Header,
    AddTodo
  },
  data() {
    return {
      //source of the todos prop: notice next line
      todos:[]
    }
  }, 
  methods:{
     /* filter() will return a new todos object, with the one that has the id of the 
     * one passed as function argument will be deleted
     * filter() is like a for loop with a condition that returns only  the items that fullfill that condition
     */
    deleteTodo(id) {
      this.todos = this.todos.filter(
        todo => todo.id !== id
      )
    },
    addTodo(newTodo){
      //return todos with the todos + added todo from the form:
        this.todos = [...this.todos, newTodo]; 
      }
    }, created() {
    // a function that fires off when the component loads, 
    // similar to component did mount in react
    // we will use axios to create a get request: which will return a promise
    // that has to be handled with .then
    // the response res, includes data property that includes all todos
    // this.todos refers to todos empty array from the data() above, 
    // which will be poppulated with the response data


    //will get all todos from the api: axios.get('https://jsonplaceholder.typicode.com/todos')
    // will get only 10 using the query parameter
    axios.get('https://jsonplaceholder.typicode.com/todos?_limit=10')
    .then(res => this.todos = res.data)
    .catch(err => console.log(err));
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
