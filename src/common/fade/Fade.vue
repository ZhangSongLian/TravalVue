<template>
  <div>
    <transition>
      <!-- 插槽，内容分发 -->
      <slot></slot>
    </transition>
  </div>
</template>

<script>
export default {
  name: 'Fade'
}
</script>

<style lang="stylus" scoped>
  .v-enter, v-leave-to
    opacity 0
  .v-enter-active, .v-leave-active
    transition opacity 0.5s
</style>
