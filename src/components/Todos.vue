<template>
    <div id="todos">
        <div class="todoItemContainer" v-for="todo in todos" v-bind:key="todo.id">
            <TodoItem v-bind:todo="todo" v-on:del-todo="$emit('del-todo', todo.id)"/>
        </div>
        <div class="todoCounter">Total Count: {{todos.length}}</div>
    </div>
</template>

<script>
    import TodoItem from "./TodoItem.vue";

    export default {
        name: "Todos",
        components: {
            TodoItem
        },
        props: ["todos"]
    }
</script>

<style scoped>
    #todos .todoCounter {
        font-size: 18px;
        font-weight: 600;
        background-color: #42b883;
        padding: 0.5em 0.5em;
        color: white;
    }
</style>