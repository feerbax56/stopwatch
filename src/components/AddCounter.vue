<template>
  <div class="addCounter">
    <div class="btnBlock">
      <button class="btnStyleNone">
        <svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" fill="currentColor" class="bi bi-plus-lg"
             viewBox="0 0 16 16">
          <path fill-rule="evenodd"
                d="M8 2a.5.5 0 0 1 .5.5v5h5a.5.5 0 0 1 0 1h-5v5a.5.5 0 0 1-1 0v-5h-5a.5.5 0 0 1 0-1h5v-5A.5.5 0 0 1 8 2Z"/>
        </svg>
      </button>
    </div>
  </div>
</template>

<script>

export default {
  name: 'AddCounter',
}
</script>

<style>
.addCounter {
  width: 225px;
  height: 120px;
  background-color: #696969;
  color: #9E9E9E;
  display: flex;
  justify-content: center;
}

.btnStyleNone {
  border: none;
  padding: 0;
  font: inherit;
  color: inherit;
  background-color: transparent;
  cursor: pointer;
}

.btnBlock {
  padding: 20px;
  display: flex;
  align-content: center;
  justify-content: center;
  gap: 50px;
}
</style>