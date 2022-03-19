<script lang="ts" setup>
import { DateTime } from 'luxon'
import { computed, onMounted, onUnmounted, ref, watch, watchEffect } from 'vue';
import CountdownTimer from "./CountdownTimer.vue";

const props = defineProps<{
  title: string
  launchDate: DateTime
}>()

const now = ref(DateTime.now())
const intervalId = ref<any>()

const diff = computed(() => props.launchDate.diff(now.value, ['days', 'hours', 'minutes','seconds']).toObject())

onMounted(() => {
   intervalId.value = setInterval(() => {
     now.value = DateTime.now()
   }, 1000)
})

onUnmounted(() => {
  clearInterval(intervalId.value)
})
</script>

<template>
   <main class="container">
      <h1 class="heading">{{ title }}</h1>
      <CountdownTimer :time="diff" />
   </main>
</template>

<style scoped>
.heading {
  text-transform: uppercase;
  font-size: 1.125rem;
  letter-spacing: .3825em;
  text-align: center;
  margin-bottom: 3.4375rem;
}

</style>