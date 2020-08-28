<template>
  <div id="app">
    <HelloWorld msg="シュルテテーブル"/>
    <Squares/>
    
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'
import Squares from './components/Squares.vue'

export default {
  name: 'App',
  components: {
    HelloWorld,
    Squares
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 40px;
}
@media screen and (max-width:580px){
  #app{
    margin-top: 0;
  }
}
</style>
