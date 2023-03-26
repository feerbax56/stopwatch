<template>
  <div class="mainBlock">
    <CounterStopwatch/>
    <CounterStopwatch/>
    <CounterStopwatch/>
    <CounterStopwatch/>
    <CounterStopwatch/>
    <CounterStopwatch/>
    <CounterStopwatch/>
    <CounterStopwatch/>
    <CounterStopwatch/>
    <CounterStopwatch/>
    <CounterStopwatch/>
  </div>

</template>

<script>
import CounterStopwatch from './components/Counter.vue'

export default {
  name: 'App',
  components: {
    CounterStopwatch
  }
}
</script>

<style>
#app {
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
  background-color: #353638;
}

@font-face {
  font-family: 'Gotham';
  src: local('Gotham'), url("../src/assets/fonts/gothampro.ttf") format("truetype");
}

body {
  background-color: #353638;
}

.mainBlock{
  width: 900px;
  display: flex;
  flex-wrap: wrap;
  gap: 50px;
  justify-content: flex-start;
  margin: 15px auto;
}
@media (max-width: 800px){
  .mainBlock{
    width: 550px;
  }
}

@media (max-width: 400px){
  .mainBlock{
    width: 250px;
  }
}
</style>
