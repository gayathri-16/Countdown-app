<template>
  <div id="app">
        
    <counter
    :year="2020"
    :month="10"
    :date="22"
    :hour="20"
    :minute="52"
    :second="30"
    :millisecond="31"
    />
    </div>
  
</template>

<script>
import counter from '@/components/counter.vue'

export default {
  name: 'App',
  components: {
  counter
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
