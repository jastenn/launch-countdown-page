<script lang="ts" setup>
import IconFacebook from './icons/IconFacebook.vue'
import IconInstagram from './icons/IconInstagram.vue';
import IconPinterest from './icons/IconPinterest.vue';

interface SocialLink {
  name: string
  url: string
  icon: any
}

const socialLinks: SocialLink[] = [
  {
    name: 'Facebook',
    url: '#',
    icon: IconFacebook
  },
  {
    name: 'Instagram',
    url: '#',
    icon: IconInstagram
  },
  {
    name: 'Pinterest',
    url: '#',
    icon: IconPinterest
  }
]
</script>

<template>
  <div class="container">
    <a v-for="link in socialLinks" class="social-link" :href="link.url" :aria-label="link.name">
      <component class="icon" :is="link.icon" />
    </a>
  </div>
</template>

<style scoped>
.container {
  width: max-content;
  margin: 0 auto;
}

.container > * {
  display: inline-block;
}
.container > * + * {
  margin-left: 1.5rem;
}

</style>

<style>
.social-link .icon > *,
.social-link .icon > *{
  transition: fill 200ms ease-out;
}

.social-link:hover .icon > *,
.social-link:focus .icon > *{
  fill: var(--primary-soft-red);
}
</style>