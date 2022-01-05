<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <HelloWorld msg="Д/З Урок №2 Vue JS"/>
    <CalculatorComp/>
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'
import CalculatorComp from './components/Calc.vue'

export default {
  name: 'App',
  components: {
    CalculatorComp,
    HelloWorld
  },
  data: () => ({
  }),
  methods: {}
}
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
