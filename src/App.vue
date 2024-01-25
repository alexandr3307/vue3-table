<template>
  <div id="app">
    <PhonebookInterface></PhonebookInterface>
  </div>
</template>

<script>
import PhonebookInterface from '@/components/PhonebookInterface'

export default {
  name: 'App',
  components: {
    PhonebookInterface
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
