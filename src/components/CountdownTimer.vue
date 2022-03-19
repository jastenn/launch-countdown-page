<template>
  <div>
    <div class="timers">
      <CountdownTimerCard label="days" :value="time.days" />
      <CountdownTimerCard label="hours" :value="time.hours" />
      <CountdownTimerCard label="minutes" :value="time.minutes" />
      <CountdownTimerCard label="seconds" :value="time.seconds" />
    </div>
  </div>
</template>

<script lang="ts" setup>
import CountdownTimerCard from "./CountdownTimerCard.vue";
import { DurationObjectUnits } from 'luxon'

const props = defineProps<{
    time: DurationObjectUnits
}>()

</script>

<style scoped>
.timers {
    display: flex;
    justify-content: space-between;
}
</style>