
<template>
  <div id="app">
     <Todocard></Todocard>
  </div>
</template>

<script>
import Todocard from './components/ToDoCard.vue'

export default {
  name: 'app',
  components: {
    Todocard
  },

  data () {
    return {
      msg: 'En effet'
    }
  }
}
</script>

<style>

  #app {
    display: flex;
    align-content: center;
    justify-content: center;
    background-color: rgb(226, 196, 26);
    height: 100vh;
  }

</style>