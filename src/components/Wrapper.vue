<script setup lang="ts">
defineProps({
  frontmatter: {
    type: Object,
    required: true,
  },
})
</script>

<template>
  <div class="prose" :class="[frontmatter.wrapperClass]" m-auto mb-8 font-bold>
    <h1>
      {{ frontmatter.display ?? frontmatter.title }}
    </h1>
  </div>
  <article>
    <slot />
  </article>
  <div v-if="$route.path !== '/'" class="prose slide-enter m-auto mb-8 mt-8 animate-delay-500 print:hidden">
    <span font-mono op50>> </span>
    <RouterLink
      :to="$route.path.split('/').slice(0, -1).join('/') || '/'"
      class="font-mono op50 hover:op75"
      v-text="'cd ..'"
    />
  </div>
</template>
