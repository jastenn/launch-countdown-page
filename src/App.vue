<script setup lang="ts">
import Countdown from './components/Countdown.vue';
import SocialLinks from './components/SocialLinks.vue';

</script>

<template>
  <div class="app">
    <Countdown title="We're launching soon" />
    <SocialLinks />
  </div>
</template>

<style>
@import url('https://fonts.googleapis.com/css2?family=Red+Hat+Text:wght@700&display=swap');

:root {
  --primary-grayish-blue: hsl(237, 18%, 59%);
  --primary-soft-red: hsl(345, 95%, 68%);

  --neutral-white: hsl(0, 0%, 100%);
  --neutral-dark-blue-1: hsl(236, 21%, 26%);
  --neutral-dark-blue-2: hsl(235, 16%, 14%);
  --neutral-dark-blue-3: hsl(234, 17%, 12%);
}

*,
*::before,
*::after {
  padding: 0;
  margin: 0;
  box-sizing: inherit;
}

html {
  font-size: 100%;
}

body {
  font-family: 'Red Hat Text', sans-serif;
  color: var(--neutral-white);
  font-size: .875rem;
  font-weight: 700;
  background-color: var(--neutral-dark-blue-3) ;
  background-image: url('./assets/images/pattern-hills.svg'), url('./assets/images/bg-stars.svg'); 
  background-repeat: no-repeat, no-repeat;
  background-position: bottom left, center;
  background-position: bottom left -5rem, center;
  background-size: 70rem, cover;
  min-height: 100vh;
}

.app {
  padding-top: 8.875rem;
}
</style>
