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
</template>
