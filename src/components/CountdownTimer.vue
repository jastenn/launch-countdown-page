<template>
  <div>
    <div :aria-label="label" class="timers">
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
import { computed } from "vue";

const props = defineProps<{
    time: DurationObjectUnits
    label: string
}>()

</script>

<style scoped>
.timers {
    display: flex;
    justify-content: space-between;
}
</style>