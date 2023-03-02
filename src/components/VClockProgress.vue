<script lang="ts" setup>
defineProps<{
  progressValue: number;
}>();
</script>

<template>
  <div class="progress__wrapper">
    <div class="progress__value" :style="{ width: `${progressValue}%` }"></div>
  </div>
</template>

<style>
.progress__wrapper {
  height: 8px;
  background-color: #2b2b2b;
  width: 95%;
  margin-top: 20px;
  border-radius: 5px;
}

.progress__value {
  height: 100%;
  background-color: aliceblue;
  border-radius: 5px;
}
</style>
