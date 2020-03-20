<template>
  <div id="app">
    <Header />
    <!-- receives the emitted todo.id from del-todo sent by the v-on from Todos.vue, deleteTodo function can now receive the todo.id
    as an argument as it was paased from Todos component up to here in App.vue component-->
    <Todos v-bind:todos = "todos" v-on:del-todo="deleteTodo"/>
    
  </div>
</template>

<script>
import Todos from './components/Todos';
import Header from './components/Layout/Header';

export default {
  name: 'App',
  components: {
    Todos,
    Header
  }, methods:{
     /* filter() will return a new todos object, with the one that has the id of the 
     * one passed as function argument will be deleted
     * filter() is like a for loop with a condition that returns only  the items that fullfill that condition
     */
    deleteTodo(id) {
      this.todos = this.todos.filter(
        todo => todo.id !== id
      )
    }

  },
  data() {
    return {
      //source of the todos prop: notice next line
      todos:[{
        id:1,
        title:"Todo one",
        completed: false
      },
      {
        id:2,
        title:"Todo two",
        completed: true
      },
      {
        id:3,
        title:"Todo three",
        completed: false
      }]
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
  margin-top: 60px;
}
</style>
