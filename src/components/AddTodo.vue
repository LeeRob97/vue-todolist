<template>
    <div id="newTodoContainer">
        <input id="newTodoText" type="text" placeholder="Add New Item" v-on:keyup="setUserDesc" ref="input"/>
        <button id="submit" v-on:click="handleSubmit">+</button>
    </div>
</template>

<script>
    import {v4} from "uuid";

    export default {
        name: "AddTodo",
        data() {
            return ({
               userDesc: "",
               id: null
            });
        },
        methods: {
            setUserDesc(e) {
                this.userDesc = e.currentTarget.value;
            },
            handleSubmit() {
                this.id = v4();

                this.$emit('add-todo', {id: this.id, desc: this.userDesc});
                this.resetUserDesc();
            },
            resetUserDesc() {
                this.userDesc = "";
                this.$refs.input.value = this.userDesc;
            }
        }
    }
</script>

<style scoped>
    #newTodoContainer {
        display: flex;
        flex-direction: row;
        height: 60px;
    }

    #newTodoContainer #newTodoText {
        box-sizing: border-box;
        height: 100%;
        border: none;
        font-size: 16px;
        width: calc(100% - 60px);
    }

    #newTodoContainer #newTodoText::placeholder {
        padding-left: 5px;
    }

    #newTodoContainer #submit {
        width: 60px;
        border: none;
        background-color: #42b883;
        font-size: 35px;
        color: white;
        cursor: pointer;
    }
</style>