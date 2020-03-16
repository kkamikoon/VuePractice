<template>
    <div id="app">
        <kkamiHeader></kkamiHeader>
        <kkamiInput></kkamiInput>
        <kkamiList></kkamiList>
        <kkamiFooter></kkamiFooter>
    </div>
</template>

<script>
import kkamiHeader from "./components/kkamiHeader.vue"
import kkamiFooter from "./components/kkamiFooter.vue"
import kkamiList   from "./components/kkamiList.vue"
import kkamiInput  from "./components/kkamiInput.vue"

export default {
  name: 'app',
  data () {
    return {
      msg: 'Welcome to Your Vue.js App'
    }
  },
  components: {
    "kkamiHeader" : kkamiHeader,
    "kkamiFooter" : kkamiFooter,
    "kkamiInput"  : kkamiInput,
    "kkamiList"   : kkamiList
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
