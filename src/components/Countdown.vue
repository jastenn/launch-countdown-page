<template>
  <main class="container">
    <h1 class="heading">{{ title }}</h1>
    <CountdownTimer :label="readableLaunchDate" :time="diff" />
  </main>
</template>

<script lang="ts" setup>
import { DateTime } from "luxon";
import { computed, onMounted, onUnmounted, ref } from "vue";
import CountdownTimer from "./CountdownTimer.vue";

const props = defineProps<{
  title: string;
  launchDate: DateTime;
}>();

const now = ref(DateTime.now());
const intervalId = ref<any>();

const diff = computed(() =>
  props.launchDate
    .diff(now.value, ["days", "hours", "minutes", "seconds"])
    .toObject()
);
const readableLaunchDate = computed(() => props.launchDate.toLocaleString());

onMounted(() => {
  intervalId.value = setInterval(() => {
    now.value = DateTime.now();
  }, 1000);
});

onUnmounted(() => {
  clearInterval(intervalId.value);
});
</script>

<style scoped>
.heading {
  text-transform: uppercase;
  font-size: 1.125rem;
  letter-spacing: 0.3825em;
  text-align: center;
  margin-bottom: 3.4375rem;
}
</style>
