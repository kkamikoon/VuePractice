<template>
    <div class="inputBox shadow">
        <input type="text" v-model="newTodoItem" placeholder="Type what you have to do" v-on:keyup.enter="addTodo">
        <span class="addContainer" v-on:click="addTodo">
            <i class="addBtn fa fa-plus" aria-hidden="true"></i>
        </span>
        <!-- <button v-on:click="addTodo">Add</button> -->

        <modal v-if="showModal" @close="showModal=false">
            <h3 slot="header">Warning</h3>
            <span slot="footer" @click="showModal=false">
                Write your work to do.
                <i class="closeModalBtn fa fa-times" aria-hidden="true"></i>
            </span>
        </modal>
    </div>
</template>

<script>
import Modal from './common/Modal.vue'

export default {
    data() {
        return {
            // It's not like placeholder
            // It is default setting of variable
            newTodoItem: "",
            showModal: false
        }
    },
    methods: {
        /*
        :function localStroage.setItem(varName, varVal):
            :varName: name of variable
            :varVal:  value of variable
         */
        addTodo() {
            //console.log(this.newTodoItem);
            if(this.newTodoItem !== "") {
                var value = this.newTodoItem && this.newTodoItem.trim();
                // to emit a signal your value to App.vue's addTodo methods
                this.$emit("addTodo", value);
                this.clearInput();
            }
            else {
                this.showModal = !this.showModal;
            }
        },
        clearInput() {
            this.newTodoItem = "";
        }
    },
    components: {
        Modal: Modal
    }
}
</script>

<style scoped>
    input:focus {
        outline: none;
    }
    .inputBox {
        background: white;
        height: 50px;
        line-height: 50px;
        border-radius: 5px;
    }
    .inputBox input {
        border-style: none;
        font-size: 0.9rem;
    }
    .addContainer {
        float: right;
        background: linear-gradient(to right, #6478FB, #8763FB);
        display: inline-block;
        width: 3rem;
        border-radius: 0 5px 5px 0;
    }
    .addBtn {
        color: white;
        vertical-align: middle;
    }
</style>