<template>
  <VHeader />
  <router-view style="min-height: calc(100vh - 48px - 78px)" />
  <Control />
  <VFooter />
</template>

<script lang="ts" setup>
import Setting from '@/../setting/setting.json'
import Control from '@/views/Control.vue'
import VFooter from '@/views/Footer.vue'
import VHeader from '@/views/Header.vue'

const CONSOLE = Setting['console'] || {}
if (CONSOLE && (CONSOLE.text || CONSOLE.img)) {
  const text = CONSOLE.text || ''
  const size = CONSOLE.size || '16px'
  const color = CONSOLE.color || ''

  const width = CONSOLE.imgWidth || '100%'
  const height = CONSOLE.imgHeight || '100%'
  const img = CONSOLE.img ? `padding-right:${width};padding-top:${height};background:url('${location.origin}/img/${CONSOLE.img}') no-repeat;background-size:100% 100%` : ''

  console.log(`%c${text}%c `, `font-size:${size};color:${color}`, img)
}
</script>

<style lang="stylus">
body
  margin 0
  -webkit-tap-highlight-color rgba(0, 0, 0, 0)
  background-image: url('@/../static/img/rei_left.png'),  url('@/../static/img/rei_right.png'), url('@/../static/img/background_empty.png')
  background-size: contain, contain, cover
  background-repeat: no-repeat
  background-attachment: fixed
  background-position: left, right, center

@media only screen and (max-width 634px) and (prefers-color-scheme dark)
  body
    background-image: url('@/../static/img/rei_left.png'), url('@/../static/img/background_empty.png')
    background-size: cover
    background-position: left, center

@media only screen and (max-width 634px) and (prefers-color-scheme light)
  body
    background-image: url('@/../static/img/rei_left.png'), url('@/../static/img/background_empty.png')
    background-size: cover
    background-position: left, center

a
  color #888
  text-decoration none

::-webkit-scrollbar
  width 7px
  height 7px

::-webkit-scrollbar-track
  box-shadow inset 0 0 6px rgba(0, 0, 0, 0.3)
  -webkit-box-shadow inset 0 0 6px rgba(0, 0, 0, 0.3)
  background-color $sub-color

::-webkit-scrollbar-thumb
  box-shadow inset 0 0 6px rgba(0, 0, 0, 0.1)
  -webkit-box-shadow inset 0 0 6px rgba(0, 0, 0, 0.1)
  background-color $main-color

::-webkit-scrollbar-thumb:active
  background-color $active-color
</style>
