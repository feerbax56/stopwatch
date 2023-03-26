<template>


  <div class="counterBlock" :class="{activeCounter: timerState==='running'}">
    <div class="timerBlock">{{ formattedTime }}</div>
    <div class="btnBlock">
      <button v-on:click="pauseTimer(), showStart()" v-if="!show" class="btnStyleNone">
        <svg xmlns="http://www.w3.org/2000/svg" width="18" height="20" fill="currentColor" class="bi bi-pause"
             viewBox="0 0 16 16">
          <path
              d="M6 3.5a.5.5 0 0 1 .5.5v8a.5.5 0 0 1-1 0V4a.5.5 0 0 1 .5-.5zm4 0a.5.5 0 0 1 .5.5v8a.5.5 0 0 1-1 0V4a.5.5 0 0 1 .5-.5z"/>
        </svg>

      </button>
      <button v-on:click="startTimer(), showPaused()" v-if="show" class="btnStyleNone">
        <svg xmlns="http://www.w3.org/2000/svg" width="17" height="20" fill="currentColor" class="bi bi-play-fill"
             viewBox="0 0 16 16">
          <path
              d="m11.596 8.697-6.363 3.692c-.54.313-1.233-.066-1.233-.697V4.308c0-.63.692-1.01 1.233-.696l6.363 3.692a.802.802 0 0 1 0 1.393z"/>
        </svg>

      </button>
      <button v-on:click="stopTimer(),  showStart()" :disabled="timerState === 'stopped'" class="btnStyleNone">
        <svg xmlns="http://www.w3.org/2000/svg" width="20" height="20" fill="currentColor" class="bi bi-stop-fill"
             viewBox="0 0 16 16">
          <path
              d="M5 3.5h6A1.5 1.5 0 0 1 12.5 5v6a1.5 1.5 0 0 1-1.5 1.5H5A1.5 1.5 0 0 1 3.5 11V5A1.5 1.5 0 0 1 5 3.5z"/>
        </svg>

      </button>
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
      show: true
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
    showStart() {
      this.show = true
    },
    showPaused() {
      this.show = false
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
        // здесь можно ускорить отсчет для проверки отображения минут и часов
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
.counterBlock {
  width: 225px;
  height: 120px;
  background-color: #696969;
  color: #9E9E9E;
}

.btnStyleNone {
  border: none;
  padding: 0;
  font: inherit;
  color: inherit;
  background-color: transparent;
  cursor: pointer;

}

.timerBlock {
  font-family: 'Gotham Pro', serif;
  font-style: normal;
  font-weight: 400;
  font-size: 22px;
  line-height: 21px;
  text-align: center;
  margin: 0 auto;
  padding: 22px;
  border-bottom: 1px solid #9E9E9E;
}

.btnBlock {
  padding: 20px;
  display: flex;
  align-content: center;
  justify-content: center;
  gap: 50px;
}

.activeCounter {
  width: 225px;
  height: 120px;
  background-color: #696969;
  color: white;
}
</style>