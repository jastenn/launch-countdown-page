<template>
  <div class="container">
    <div class="digit" :data-digit-before="formatNumber(value + 1)" :data-digit-after="formatNumber(value)">
      <!-- before -->
      <div class="card" ref="card">

        <div class="card-face card-face-front">
          <span>{{ formatNumber(value + 1) }}</span>
        </div>

        <div class="card-face card-face-back">
          <span>{{ formatNumber(value) }}</span>
        </div>
      </div>
      <!-- after -->
    </div>
    <p class="label">{{ label }}</p>
  </div>
</template>

<script setup lang="ts">
import { ref, watchEffect } from 'vue';

const props = withDefaults(
  defineProps<{
    value: number;
    label: string;
  }>(),
  {
    value: 0,
  }
);

const card = ref<HTMLDivElement>()

const formatNumber = (val: number) => (Math.floor(val)).toLocaleString('en-US', {minimumIntegerDigits: 2, useGrouping:false})

watchEffect(() => {
  if(props.value === undefined) return
  if(!card.value) return

  resetAnimation(card.value)
})

const resetAnimation = (el: HTMLElement) => {
  el.style.animation = 'none';
  el.offsetHeight; 
  (el.style.animation as any) = null; 
}

</script>

<style scoped>
.container {
  --container-height: 4.25rem;
  --upperTextColor: #D05574;
  --lowerTextColor: var(--primary-solf-red);
  --radius: 0.13589em;
  font-size: 2.25rem;
  color: var(--primary-soft-red);
  height: var(--container-height);
  width: 4.375rem;
  border-radius: var(--radius);
  box-shadow: 0 2px 1px rgba(0, 0, 0, .5);
}

.label {
  font-size: 0.4375rem;
  letter-spacing: 0.34286em;
  color: var(--primary-grayish-blue);
  text-transform: uppercase;
  text-align: center;
  margin-top: .75rem;
}


.digit {
  position: relative;
  height: 100%;
}

.digit::before,
.digit::after {
  --translateX: 0%;
  text-align: center;
  display: flex;
  justify-content: center; 
  align-items: center;
  position: absolute;
  z-index: -1;
  overflow: hidden;
  height: 50%;
  width: 100%;
  border-radius: var(--radius);
  transform: translate(var(--translateX, 0), var(--translateY, 0));
}

.digit::before {
  content: attr(data-digit-before);
  background-color: var(--card-bg-lower);
  box-shadow: inset 0 1px 3px rgba(0, 0, 0, .25);
  bottom: 0;
  padding-bottom: .875em;
}

.digit::after {
  content: attr(data-digit-after);
  color: var(--upperTextColor);
  background-color: var(--card-bg-upper);
  box-shadow: inset 0 -1px 3px rgba(0, 0, 0, .25);
  top: 0;
  padding-top: .875em;
}

.card {
  transform-origin: bottom;
  height: 50%;
  transform-style: preserve-3d;
  animation: flip .7s ease-out forwards;
}

@keyframes flip {
  from {
    transform: rotateX(0deg);
  }
  90% {
    transform: rotateX(180deg);
  }
  to {
    transform: rotateX(180deg);
  }
}
/* .card.flipped {
  transform: rotateX(180deg);
} */

.card-face {
  text-align: center;
  position: absolute;
  top: 0;
  left: 50%;
  height: 100%;
  width: 100%;
  overflow: hidden;
  transform: translate(-50%, 0) rotateY(var(--rotateY, 0deg)) rotateZ(var(--rotateZ, 0deg));
  border-radius: var(--radius);
}

.card-face-front {
  color: var(--upperTextColor);
  background-color: var(--card-bg-upper);
  box-shadow:inset 0 1px 3px rgba(0, 0, 0, .25);
  
  backface-visibility: hidden;
}

.card-face-back {
  background-color: brown;
  background-color: var(--card-bg-lower);
  box-shadow:inset 0 1px 3px rgba(0, 0, 0, .25);
  --rotateY: 180deg;
  --rotateZ: 180deg;
  backface-visibility: hidden;
}

.card-face-back > span {
  transform: translateY(-50%);
  display: block;
}

.card-face-front > span {
  display: block;
  position: absolute;
  bottom: 0;
  left: 50%;
  transform: translate(-50%, 50%);
}
</style>
