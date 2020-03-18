<template>
    <div id="app">
        <kkamiHeader></kkamiHeader>
        <kkamiInput v-on:addTodo="addTodo"></kkamiInput>
        <kkamiList v-bind:propsdata="todoItems" @removeTodo="removeTodo"></kkamiList>
        <kkamiFooter v-on:removeAll="clearAll"></kkamiFooter>
    </div>
</template>

<script>
import kkamiHeader from "./components/kkamiHeader.vue"
import kkamiInput  from "./components/kkamiInput.vue"
import kkamiList   from "./components/kkamiList.vue"
import kkamiFooter from "./components/kkamiFooter.vue"

export default {
    data() {
        return {
            todoItems: []
        }
    },
    methods: {
        clearAll(){
            localStorage.clear();
            this.todoItems = [];
        },
        addTodo(todoItem) {
            localStorage.setItem(todoItem, todoItem);
            this.todoItems.push(todoItem);
        },
        removeTodo(todoItem, index) {
            // console.log(todoItem, index);
            localStorage.removeItem(todoItem);
            this.todoItems.splice(index, 1);
        }
    },
    created() {
        if (localStorage.length > 0) {
            for (var i=0; i<localStorage.length; i++){
                this.todoItems.push(localStorage.key(i));
            }
        }
    },
    components: {
        "kkamiHeader" : kkamiHeader,
        "kkamiInput"  : kkamiInput,
        "kkamiList"   : kkamiList,
        "kkamiFooter" : kkamiFooter
    }
}
</script>

<style>
    body {
        text-align: center;
        background-color: #f6f6f6;
    }
    input {
        border-style: groove;
        width: 200px;
    }
    button {
        border-style: groove;
    }
    .shadow {
        box-shadow: 5px 10px 10px rgba(0, 0, 0, 0.03);
    }
</style>
