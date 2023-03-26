<template>


  <div class="stopwatch">
    <div>{{ formattedTime }}</div>
    <div>
      <button v-on:click="startTimer" :disabled="timerState === 'running'">start</button>
      <button v-on:click="pauseTimer">pause</button>
      <button v-on:click="stopTimer" :disabled="timerState === 'stopped'">stop</button>
    </div>
  </div>
</template>

<script>

export default {
  name: 'CounterStopwatch',
  data() {
    return {
      currentTime: 0,
      formattedTime: "0",
      timerState: 'stopped',
      timer: undefined,
    }
  },
  methods: {
    startTimer() {
      if (this.timerState !== 'running') {
        this.tick();
        this.timerState = 'running';
      }
    },
    pauseTimer() {
      this.timerState = 'paused'
      window.clearInterval(this.timer)
    },
    stopTimer() {
      window.clearInterval(this.timer)
      this.currentTime = 0
      this.formattedTime = "0"
      this.timerState = 'stopped'
    },
    tick() {
      this.timer = setInterval(() => {
        this.currentTime++
        this.formattedTime = this.formatTime(this.currentTime)
      }, 1000)
    },
    formatTime(seconds) {
      let createdTime = new Date(null)
      createdTime.setSeconds(seconds)
      // количество знаков в зависимости от наличия минут и часовых значений
      if (seconds < 59) {
        return createdTime.toISOString().substring(19, 17)
      } else if (seconds < 3599) {
        return createdTime.toISOString().substring(19, 14)
      } else {
        return createdTime.toISOString().substring(19, 11)
      }
      // время перегоняется в строку и вырезается лишнее
      // let fullTime = createdTime.toISOString().substring(19, 11)
      // console.log(fullTime)
      // return fullTime
    },
  }
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