<script lang="ts" setup>
import { computed, onMounted, reactive } from "vue";
import VClockProgress from "./VClockProgress.vue";

const currentTime = reactive({
  h: 0,
  m: 0,
  s: 0,
});

onMounted(() => {
  setInterval(() => {
    currentTime.h = new Date().getHours();
    currentTime.m = new Date().getMinutes();
    currentTime.s = new Date().getSeconds();
  }, 1000);
});

const dayProgress = computed(() => {
  const fullDayInSecs = 24 * 60 * 60;
  const currentTimeInSecs = currentTime.h * 60 * 60 + currentTime.s;

  return Math.floor((currentTimeInSecs / fullDayInSecs) * 100);
});
</script>

<template>
  <div class="clock__wrapper">
    <div class="clock__digits">
      {{ currentTime.h }}:{{ currentTime.m }}:{{ currentTime.s }}
    </div>

    <v-clock-progress :progressValue="dayProgress"></v-clock-progress>
  </div>
</template>

<style>
.clock__wrapper {
  display: flex;
  align-items: center;
  justify-content: center;
  height: 80vh;
  font-size: 70px;
  flex-direction: column;
  width: 350px;
}
</style>
