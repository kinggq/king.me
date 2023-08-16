<script setup lang="ts">

</script>

<template>
  <header flex justify-between>
    <RouterLink to="/" />
    <nav class="nav">
      <div />
      <div class="right">
        <RouterLink to="/posts" title="Blog">
          <span>Blog</span>
          <div i-ri-article-line md:hidden />
        </RouterLink>
        <RouterLink to="/projects" title="Projects">
          <span class="lt-md:hidden">Projects</span>
          <div i-ri-lightbulb-line class="md:hidden" />
        </RouterLink>
        <RouterLink to="/demos" title="Demos">
          <span class="lt-md:hidden">Demos</span>
          <div i-ri-screenshot-line class="md:hidden" />
        </RouterLink>
        <a href="https://twitter.com/King_bgq" target="_blank" title="Twitter" class="lt-md:hidden">
          <feather-twitter />
        </a>
        <a href="https://github.com/kinggq" target="_blank" title="GitHub" class="lt-md:hidden">
          <div i-uil-github-alt />
        </a>
        <toggle-theme />
      </div>
    </nav>
  </header>
</template>

<style scoped>
.nav {
  padding: 2rem;
  width: 100%;
  display: grid;
  grid-template-columns: auto max-content;
  box-sizing: border-box;
}
.nav .right {
  display: grid;
  grid-gap: 1.2rem;
  grid-auto-flow: column;
}
.nav > * {
  margin: auto;
}

.nav a {
  cursor: pointer;
  text-decoration: none;
  color: inherit;
  transition: opacity 0.2s ease;
  opacity: 0.6;
  outline: none;
}
.nav a:hover {
  opacity: 1;
  text-decoration-color: inherit;
}
.nav .right > * {
  margin: auto;
}
</style>
