<template>
    <section>
        <ul>
            <!--
            <li>To Do No.01</li>
            <li>To Do No.02</li>
            <li>To Do No.03</li>
            -->
            <!--
            It will occured some error that there is no v-bind:key.
            Should add v-bind:key="[The Item Key Value]"
                Good : <li v-for="todoItem in todoItems">
                Bad  : <li v-for="todoItem in todoItems" v-bind:key="todoItem">
            
            Comment by https://beomy.tistory.com/52
            -->
            <li v-for="(todoItem, index) in todoItems" v-bind:key="todoItem" class="shadow">
                <i class="checkBtn fa fa-check" aria-hidden="true"></i>
                {{ todoItem }}
                <span class="removeBtn" type="button" @click="removeTodo(todoItem, index)">
                    <i class="fa fa-trash-o" aria-hidden="true"></i>
                </span>
            </li>
        </ul>
    </section>
</template>

<script>
export default {
    data() {
        return {
            todoItems: []
        }
    },
    created() {
        if (localStorage.length > 0) {
            for (var i=0; i<localStorage.length; i++){
                this.todoItems.push(localStorage.key(i));
            }
        }
    },
    methods: {
        removeTodo(todoItem, index) {
            // console.log(todoItem, index);
            localStorage.removeItem(todoItem);
            this.todoItems.splice(index, 1);
        }
    }
}
</script>

<style>
    ul {
        list-style-type: none;
        padding-left: 0px;
        margin-top: 0;
        text-align: left;
    }

    li {
        display: flex;
        min-height: 50px;
        height: 50px;
        line-height: 50px;
        margin: 0.5rem 0;
        padding: 0 0.9rem;
        background: white;
        border-radius: 5px;
    }

    .checkBtn {
        line-height: 45px;
        color: #62acde;
        margin-right: 5px;
    }

    .removeBtn {
        margin-left: auto;
        color: #de4343;
    }
</style>