<template>
  <div class="app">
    <main>
      <Countdown :launch-date="launchDate" title="We're launching soon" />
    </main>

    <footer class="footer">
      <SocialLinks class="socials" />
      <Attribution />
    </footer>
  </div>
</template>

<script setup lang="ts">
import Countdown from './components/Countdown.vue';
import Attribution from './components/Attribution.vue';
import SocialLinks from './components/SocialLinks.vue';
import { DateTime } from 'luxon'

const launchDate = DateTime.now().plus({ days: 14 })
</script>


<style>
@import url('https://fonts.googleapis.com/css2?family=Red+Hat+Text:wght@700&display=swap');

:root {
  --primary-grayish-blue: hsl(237, 18%, 59%);
  --primary-soft-red: hsl(345, 95%, 68%);
  --neutral-white: hsl(0, 0%, 100%);

  --neutral-dark-blue-1: hsl(236, 21%, 26%);
  --neutral-dark-blue-2: hsl(235, 16%, 14%);
  --neutral-dark-blue-3: hsl(234, 17%, 12%);

  --card-bg-upper: hsl(245, 23%, 22%);
  --card-bg-lower: hsl(235, 19%, 25%);
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
  box-sizing: border-box;
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
  position: relative;
  min-height: 100vh;
}

.app {
  width: 87%;
  max-width: 42.94rem;
  margin: 0 auto;
  padding-top: 8.875rem;
}

.footer {
  color: var(--primary-grayish-blue);
  position: absolute;
  bottom: 1.25rem;
  left: 50%;
  transform: translateX(-50%);
}

.footer .socials {
  margin-bottom: 1rem;
}
@media (min-width: 800px) {
  body {
    background-position: bottom, center;
    background-size: contain, cover;
  }
}
</style>
