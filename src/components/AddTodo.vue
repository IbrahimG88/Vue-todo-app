<template>
<div>
    <!-- on submit event call addTodo()-->
    <form @submit="addTodo">
        <!-- v-model for data binding, bound to title from data() function in the script -->
        <input type="text" name="title" v-model="title" placeholder="Add Todo...">
        <input type="submit" value="Submit" />
    </form>
</div>
    
</template>

<script>
import { v4 as uuidv4 } from 'uuid';

export default {
    name:"AddTodo",
    data(){
        return {
            title: ""
        }
    },
    methods:{
        // the e event refers to the form returned data
        addTodo(e) {
            e.preventDefault();
            const newTodo = {
                //uuid uses generated id from  package uuid
                id: uuidv4(),
                title: this.title,
                completed: false
            }
            this.$emit('add-todo', newTodo);
            // to reset form title
            this.title = '';
  
        }
    }
}

</script>

<style>

</style>