<template>
  <body id="app">
    <Header></Header>
    <Gallery>
      
    </Gallery>
    <!-- <HelloWorld msg="Welcome to Your Vue.js App"/> -->
  </body>
</template>

<script>
// import HelloWorld from './components/HelloWorld.vue'
import Header from './components/Header.vue'
import Gallery from './components/Gallery.vue'


export default {
  name: 'App',
  components: {
    // HelloWorld,
    Header,
    Gallery
  }
}
</script>

<style>

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  /* text-align: center; */
  color: #727272;
  margin-top: 60px;
  box-sizing: border-box;
}

body{
  background: #222;
}
</style>
