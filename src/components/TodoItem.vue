<template>
    <!-- add a conditional for completed true or false -->
    <div class="todo-item" v-bind:class="{'is-complete': todo.completed}">
        <p>
        <!-- v-on adds an event, variations: change, submit, click, accepts a method -->
        <input type="checkbox" v-on:change="markComplete"/>
        {{todo.title}}
        <!-- when clicked emit an event called 'del-todo', that includes the value of todo.id -->
        <button class="del" @click="$emit('del-todo', todo.id)">x</button>
        </p>
    </div>
</template>
    
<script>
    export default {
        name: "TodoItem",
        props:["todo"], 
        //object of functions
        methods: {
            markComplete() {
                //console.log(123)
                // invert using the not operator the value of comleted
                this.todo.completed = !this.todo.completed;
            }
            }

    }
</script>

<style>
.is-complete {
    text-decoration: line-through;
}
</style>