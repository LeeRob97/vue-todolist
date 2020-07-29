<template>
  <div id="app">
      <Header />
      <AddTodo v-on:add-todo="addTodo"/>
      <Todos v-bind:todos="todos" v-on:del-todo="deleteTodo"/>
  </div>
</template>

<script>
    import Header from "./components/layout/Header";
    import AddTodo from "./components/AddTodo";
    import Todos from "./components/Todos";

    export default {
        name: 'App',
        components: {
            Header,
            AddTodo,
            Todos
        },
        data() {
            return {
                todos: [
                    {
                        id: 1,
                        title: `Todo One`,
                        completed: true
                    },
                    {
                        id: 2,
                        title: `Todo Two`,
                        completed: false
                    },
                    {
                        id: 3,
                        title: `Todo Three`,
                        completed: false
                    },
                ]
            }
        },
        methods: {
            deleteTodo(id) {
                this.todos = this.todos.filter(({id: todoID}) => todoID !== id);
            },
            addTodo({id, desc}) {
                this.todos.push({
                    id: id,
                    title: desc,
                    completed: false
                });
            }
        }
    }
</script>

<style>
    * {
        box-sizing: border-box;
        margin: 0;
        padding: 0;
    }

    body {
        line-height: 1.4;
    }

    button:focus, input:focus, textarea:focus, select:focus{
        outline: none;
    }

    #app {
        max-width: 960px;
        margin: 0 auto;
    }
</style>
