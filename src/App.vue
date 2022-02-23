<template>
  <div id="app">
    <MyHeader />
    <MainContent />
    
  </div>
</template>

<script>


import MyHeader from './components/MyHeader.vue';
import MainContent from './components/MainContent.vue'

export default {
  name: 'App',
  components: {
    MyHeader,
    MainContent,
   },
   


    

}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  

}
</style>
