<template>
  <div class="attribution">
    Challenge by
    <a href="https://www.frontendmentor.io?ref=challenge" target="_blank"
      >Frontend Mentor</a
    >. Coded by <a href="https://github.com/jastenn" target="_blank">Justine Aviso</a>.
  </div>
</template>

<script setup lang="ts"></script>

<style scoped>
.attribution {
  font-size: .75rem;
  text-align: center;
}

.attribution a {
  color: var(--neutral-white);
  transition: color 200ms ease-out;
  outline: none;
}

.attribution a:hover,
.attribution a:focus {
  color: var(--primary-soft-red);
}

@media (min-width: 800px) {
  .attribution {
    font-size: 1rem;
  }
}

</style>
