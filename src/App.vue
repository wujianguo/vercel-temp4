<template>
  <img alt="Vue logo" src="./assets/logo.png">
  <p>{{ data.data }}</p>
  <p>{{ data2.data }}</p>

  <HelloWorld msg="Welcome to Your Vue.js App" />
</template>

<script>
import axios from 'axios'
import HelloWorld from './components/HelloWorld.vue'

export default {
  name: 'App',
  components: {
    HelloWorld
  },
  data() {
    return {
      data: { data: 'Loading...' },
      data2: { data: 'Loading2...' }
    }
  },
  mounted() {
    axios.get('/api/hello').then((response) => {
      this.data = response.data
    })
    axios.get('/api/hello/foo').then((response) => {
      this.data2 = response.data
    })
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
  margin-top: 60px;
}
</style>
