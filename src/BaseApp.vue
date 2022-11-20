<script setup>
// This starter template is using Vue 3 <script setup> SFCs
// Check out https://vuejs.org/api/sfc-script-setup.html#script-setup
import {ref} from 'vue'

const iframe = ref(null)
let watcher = null
let lastHeight = null
let targetHeight = null

const resizeIframe = () => {
  const iframeHTML = iframe.value.contentDocument.querySelector('html')
  if (iframeHTML) {
    targetHeight = iframeHTML.getBoundingClientRect().height

    if (lastHeight !== targetHeight) {
      lastHeight = targetHeight
      console.log(`change iframe height to ${lastHeight}`);
      iframe.value.style.height = lastHeight + 'px'
    }
  }
}

const watch = () => {
  cancelAnimationFrame(watcher)
  resizeIframe()
  watcher = requestAnimationFrame(watch)
}

watcher = requestAnimationFrame(watch)

</script>

<template>
  <h1 class="header">Looks the same as the index page</h1>
  <iframe ref="iframe" src="http://127.0.0.1:5173/child.html" frameborder="0"></iframe>
</template>

<style scoped lang="scss">
iframe {
  width: 100%;
  height: 100%;
}
</style>
