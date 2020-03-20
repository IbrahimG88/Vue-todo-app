<template>
<div>
<div v-bind:key="todo.id" v-for="todo in todos">
    <h1>Todos</h1>
    <h3>{{ todo.title }}</h3>
    <!-- v-bind adds a prop, here it is using the todo from the for loop   -->
    <!-- receives the emitted variable del-todo from todoItem component and emits it further up -->
    <TodoItem v-bind:todo="todo" v-on:del-todo="$emit('del-todo',todo.id)" />
</div>
</div>
</template>

<script>
import TodoItem from './TodoItem.vue';
export default {
    name: 'Todos',
    components:{
        TodoItem
    },
    props:["todos"]
}
</script>

<style scoped>

</style>