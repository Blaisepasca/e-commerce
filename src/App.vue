<template>
<div id="app">
  
  <homepagerestaurant/>
  </div>
</template>

<script>
import Homepagerestaurant from './components/page/HomeRestaurant.vue'


export default {
  name: 'App',
  components:{
    Homepagerestaurant
    
  }
    
}
</script>

<style>
@import url('./style/reset.css');
@import url('https://fonts.googleapis.com/css2?family=Roboto%3Awght%40300%3B400%3B700&display=swap');
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  padding: 5px 10px;
  
}
</style>
