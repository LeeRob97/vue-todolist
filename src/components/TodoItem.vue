<template>
    <div class="todoItem">
        <input type="checkbox" v-on:change="markComplete" v-bind:checked="todo.completed"/>
        <div class="desc" v-bind:completed="todo.completed">{{todo.title}}</div>
        <button class="delete" v-on:click="$emit('del-todo', todo.id)">x</button>
    </div>
</template>

<script>
    export default {
        name: "TodoItem",
        props: ["todo"],
        methods: {
            markComplete() {
                this.todo.completed = !this.todo.completed;
            }
        }
    }
</script>

<style scoped>
    .todoItem {
        display: flex;
        flex-direction: row;
        align-items: center;
        background: #f4f4f4;
        padding: 10px;
        border-bottom: 1px dotted #ccc;
    }

    .todoItem .desc {
        font-size: 20px;
    }

    .todoItem .desc[completed="true"] {
        text-decoration: line-through;
    }

    .todoItem input {
        margin-right: 10px;
        height: 15px;
        width: 15px;
    }

    .todoItem .delete {
        background: #ff0000;
        color: #fff;
        border: none;
        padding: 5px 9px;
        border-radius: 50%;
        font-size: 18px;
        line-height: 18px;
        font-weight: 600;
        cursor: pointer;
        margin: 0 15px 0 auto;
    }
</style>