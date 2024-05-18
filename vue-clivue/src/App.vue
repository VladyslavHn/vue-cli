<template>
  <div id="app">
    <ApartmentsList :items="apartments" />
  </div>
</template>

<script>

import ApartmentsList from './components/Apartments/ApartmentsList'
import apartments from './components/Apartments/apartments.js'

export default {
  name: 'App',
  components: {
    ApartmentsList
  },
  data() {
    return {
      apartments,
      
    }
  }
}
</script>

<style>
#app {
  font-family: Montserrat, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
