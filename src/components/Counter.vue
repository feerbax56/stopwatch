<template>


  <div class="stopwatch">
    <div>{{ currentTime }}</div>
    <div>
      <button v-on:click="startTimer">start/pausa</button>
      <button v-on:click="stopTimer">stop</button>
    </div>
  </div>
</template>

<script>

export default {
  name: 'CounterStopwatch',
  data() {
    return{
      currentTime: 0,
      timer: null,
    }
  },
 methods: {
    startTimer() {
      this.timer = setInterval(() => {
        this.currentTime++
      }, 1000)
    },
    stopTimer() {
      clearTimeout(this.timer)
    },
  },
  watch: {
    currentTime(time) {
      if (time === 0) {
        this.stopTimer()
      }
    }
  },
}
</script>

<style>
.stopwatch {
  width: 255px;
  height: 120px;
  background-color: #696969;
  color: #9E9E9E;
}

</style>