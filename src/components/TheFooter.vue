<script setup lang="ts">
const vTypewriterSingle = {
  mounted(el: HTMLElement) {
    const lib = el
    let cursor_timer: any = null // 光标计时器，需要被其它函数调用，所以声明在全局作用域

    function cursor() {
      clearInterval(cursor_timer) // 调用前清除光标计时器
      cursor_timer = setInterval(() => {
        lib.classList.toggle('cursor') // 光标闪烁
      }, 500)
    }

    const say = lib.innerHTML
    function again() {
      lib.innerHTML = ''
      const says = say // 用于删除
      let num = 0 // 用于累加遍历字符串
      let text = '' // 用于输出在屏幕上
      lib.innerHTML = ''
      const timer = setInterval(() => {
        clearInterval(cursor_timer) // 禁止光标闪烁
        lib.classList.add('cursor')
        text += say[num] // 遍历输出的文字
        lib.innerHTML = text // 输出在屏幕上
        num++

        if (num >= say.length) {
          // 如果文字输出完毕
          cursor() // 调用光标闪烁
          clearInterval(timer) // 清除用于输出文字的计时器
          setTimeout(() => {
            // 文字显示完三秒后
            // clearInterval(cursor_timer) // 禁止光标闪烁
            // const delText_timer = setInterval(() => {
            //   // 开始调用删除文字的计时器
            //   says = says.substr(0, says.length - 1) // 逐个清除末尾文字
            //   lib.innerHTML = says // 每次删除一个字，输出在屏幕上
            //   if (says.length <= 0) {
            //     // 如果删除完毕
            //     clearInterval(delText_timer) // 清除用于删除文字的计时器
            //     cursor() // 调用光标闪烁
            //     setTimeout(() => {
            //       again() // 循环上面的过程
            //     }, 10000)
            //   }
            // }, 100)
          }, 2000)
        }
      }, 100)
    }
    again()
  },
}
</script>

<template>
  <div class="prose m-auto mb-6 mt-10 flex">
    <span class="text-sm op50">
      <a target="_blank" href="https://github.com/antfu" style="color:inherit">
        <div v-typewriterSingle class="TypewriterSingle cursor">特别鸣谢 @Anthony Fu</div>
      </a></span>
    <div class="flex-auto" />
  </div>
</template>

<style scoped>
.TypewriterSingle {
  --size: 14px;
  height: var(--size);
  line-height: var(--size);
  padding-right: 0.1em;
  font-size: var(--size);
  border-right: 1px solid transparent;
  margin: 1em 0;
}

.cursor {
  border-right-color: currentColor;
}
</style>
