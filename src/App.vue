<template>
  <!-- <img alt="Vue logo" src="./assets/logo.png"> -->
  <!-- <HelloWorld msg="Welcome to Your Vue.js App"/> -->
  <SpaceGallery />
</template>

<script>
// import HelloWorld from './components/HelloWorld.vue'
import SpaceGallery from "./components/SpaceGallery.vue";

export default {
  name: "App",
  components: {
    // HelloWorld,
    SpaceGallery,
  },
};
</script>

<style lang="stylus">
*
  margin 0
  padding 0
  box-sizing border-box
#app
  font-family Avenir, Helvetica, Arial, sans-serif
  -webkit-font-smoothing antialiased
  -moz-osx-font-smoothing grayscale
  text-align center
  color #2c3e50
  background :url(./assets/img/milky_way.jpeg)
  background-size cover
  min-height 100vh
</style>
