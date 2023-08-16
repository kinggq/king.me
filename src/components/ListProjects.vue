<script setup lang="ts">
defineProps<{ projects: Record<string, any[]> }>()

function slug(name: string) {
  return name.toLowerCase().replace(/[\s\\\/]+/g, '-')
}
</script>

<template>
  <div class="mx-auto max-w-300">
    <div
      v-for="key, cidx in Object.keys(projects)" :key="key" slide-enter
      :style="{ '--enter-stage': cidx + 1 }"
    >
      <h4 :id="slug(key)" class="mb-2 mt-15 text-center font-bold op75">
        {{ key }}
      </h4>
      <div
        class="project-grid mx-auto max-w-500 w-max py-2"
        grid="~ cols-1 md:cols-2 gap-4"
        :class="projects[key].length === 1 ? 'flex' : projects[key].length > 2 ? 'lg:grid-cols-3' : ''"
      >
        <a
          v-for="item, idx in projects[key]"
          :key="idx"
          class="item relative flex items-center"
          :href="item.link"
          target="_blank"
          :class="!item.link ? 'opacity-0 pointer-events-none h-0 -mt-8 -mb-4' : ''"
          :title="item.name"
        >
          <div v-if="item.icon" class="pr-5 pt-2">
            <div :class="[item.icon]" />
          </div>
          <div class="flex-auto">
            <div class="text-normal">{{ item.name }}</div>
            <div class="desc text-sm font-normal opacity-50" v-html="item.desc" />
          </div>
        </a>
      </div>
    </div>
    <div class="prose mx-auto mt10 pb5 text-center">
      <p op75>
        <em>
          Thanks for getting interested in my works!

        </em>
      </p>
    </div>
  </div>
</template>

<style scoped>
.project-grid a.item {
  background: transparent;
  font-size: 1.1rem;
  width: 350px;
  max-width: 100%;
  padding: 0.5rem 0.875rem 0.875rem;
  border-radius: 6px;
}

.project-grid a.item:hover {
  background: #88888811;
}
</style>
