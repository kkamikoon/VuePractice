<template>
    <div class="inputBox shadow">
        <input type="text" v-model="newKKAMIItem" placeholder="Type what you have to do" v-on:keyup.enter="addItem">
        <span class="addContainer" v-on:click="addItem">
            <i class="addBtn fa fa-plus" aria-hidden="true"></i>
        </span>
        <!-- <button v-on:click="addItem">Add</button> -->
    </div>
</template>

<script>
export default {
    data() {
        return {
            // It's not like placeholder
            // It is default setting of variable
            newKKAMIItem: ""
        }
    },
    methods:{
        /*
        :function localStroage.setItem(varName, varVal):
            :varName: name of variable
            :varVal:  value of variable
         */
        addItem() {
            //console.log(this.newKKAMIItem);
            if (this.newKKAMIItem !== ""){
                // Eliminate White-Space Character front and end.
                var value = this.newKKAMIItem && this.newKKAMIItem.trim();
                localStorage.setItem("varName", this.newKKAMIItem);
                // Clearing Input Value - custom function
                this.clearInput();
            }
        },
        clearInput() {
            this.newKKAMIItem = "";
        }
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