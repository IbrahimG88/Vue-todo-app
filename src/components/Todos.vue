<template>
<div>
<div v-bind:key="todo.id" v-for="todo in todos">
    <h1>Todos</h1>
    <h3>{{ todo.title }}</h3>
    <!-- v-bind adds a prop, here it is using the todo from the for loop   -->
    <TodoItem v-bind:todo="todo" />
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