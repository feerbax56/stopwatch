<template>
  <div class="mainBlock">
    <div v-for="counter in counters" :key="counter.id">
      <CounterStopwatch :key="counter.id"/>
    </div>

    <AddCounter @addCounter="addCounter"/>
  </div>

</template>

<script>
import CounterStopwatch from './components/Counter.vue'
import AddCounter from './components/AddCounter.vue'
export default {
  name: 'App',
  components: {
    CounterStopwatch,
    AddCounter,
  },
  data(){
    return{
      counters: [{id: 1},],
    }
  },
  methods: {
    addCounter(){
      let id = Math.random()
      this.counters.push({id})
    }
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
