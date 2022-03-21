<template>
  <div class="Loading">
    <div class="back"></div>
    <div class="loader"></div>
    <div class="pumpingText">
      <span>L</span>
      <span>o</span>
      <span>a</span>
      <span>d</span>
      <span>i</span>
      <span>n</span>
      <span>g</span>
    </div>
  </div>
</template>
<script>
export default {
  name: 'Loading',
  data () {
    return {
    }
  },
}
</script>
<style lang="scss">
@import '@/scss/base.scss';
@import '@/scss/loading.scss';
</style>