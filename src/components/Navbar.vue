<script setup lang="ts">
const vTextHoverColor = {
  mounted(el: HTMLElement, { value = 'black' }) {
    // 需要给父盒子加相对定位或绝对定位
    const mask = document.createElement('div')
    const line = document.createElement('div')
    mask.innerHTML = el.innerHTML
    mask.style.cssText = `
      z-index: 9;
      position: absolute;
      top: 0;
      left: 0;
      color: #fff;
      background-color: ${value};
      transition: all 0.35s;
      text-shadow: initial;
      -webkit-background-clip: text;
      clip-path: circle(75% at 50% 50%);
    `
    const line_height = el.offsetHeight / 8
    line.style.cssText = `
      z-index: 9;
      position: absolute;
      width: 0%;
      height: ${line_height}px;
      bottom: 0;
      color: transparent;
      background-color: ${value};
      transition: all 0.35s;
      left: 50%;
      transform: translate(-50%,5px);
      border-radius: ${line_height}px;
    `
    window.addEventListener('resize', () => {
      const line_height = el.offsetHeight / 20
      line.style.height = `${line_height}px`
      line.style.borderRadius = `${line_height}px`
    })

    el.appendChild(mask)
    el.appendChild(line)
    el.addEventListener('mouseenter', () => {
      mask.style.clipPath = 'circle(0% at 50% 50%)'
      line.style.width = '100%'
    })
    el.addEventListener('mouseleave', () => {
      mask.style.clipPath = 'circle(75% at 50% 50%)'
      line.style.width = '0%'
    })
  },
}
</script>

<template>
  <header flex items-center justify-between>
    <RouterLink to="/" m-5>
      <div class="TextHoverColor">
        <h1 v-textHoverColor="'gray'" text="20px gray-500" font-bold>
          King
        </h1>
      </div>
    </RouterLink>
    <nav class="nav">
      <div />
      <div class="right">
        <RouterLink to="/posts" title="Blog">
          <span class="lt-md:hidden">Blog</span>
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
.TextHoverColor {
  position: relative;
  font-size: 10vw;
  color: #3498db;
  cursor: pointer;
  user-select: none;
}
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
