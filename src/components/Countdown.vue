<script lang="ts" setup>
import CountdownTimer from "./CountdownTimer.vue";

const props = defineProps<{
  title: string
}>()

</script>

<template>
   <main class="container">
    <h1 class="heading">{{ title }}</h1>
    <CountdownTimer />
   </main>
</template>

<style scoped>
.container {
  width: 87%;
  max-width: 42.94rem;
  margin: 0 auto;
}
.heading {
  text-transform: uppercase;
  font-size: 1.125rem;
  letter-spacing: .3825em;
  text-align: center;
}

</style>