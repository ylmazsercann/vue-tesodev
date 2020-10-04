<template>
  <div id="app">
    <HomePage msg="TESODEV Search Console"/>
  </div>
</template>

<script>
import HomePage from './components/HomePage.vue'

export default {
  name: 'App',
  components: {
    HomePage
  }
}
</script>

<style lang="less">

#app {
  padding: 0;
	margin: 0;
	box-sizing: border-box;
	outline: 0;
}

body {
  padding: 0;
	margin: 0;
	box-sizing: border-box;
  outline: 0;
  font-family: 'Baloo Tammudu 2', cursive;
}


</style>
