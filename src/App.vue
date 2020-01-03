<template>
  <div id="app" class="container">
    
   <interface></interface>
    
  </div>
</template>



<script>
import Interface from "./components/Interface"



export default {
  name: 'app',
  components: {
    interface:Interface
  
  }
}
</script>






<style>



div {
  text-align: center;
}


#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
