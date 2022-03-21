<template>
  <div class="connections">
    <div class="connect">
        <span id="top">Connect</span>
        <div class="items">
            <div class="one">
                    <div class="phone"><i class="fas fa-phone"></i><span> 010-4437-0162</span></div>
                <div class="naver"><i class="fas fa-envelope"></i><span> lunilun310@gamil.com</span></div>
                <div class="google"><i class="fas fa-envelope"></i><span> ekqlscl94@naver.com</span></div>
                <div class="kakao"><i class="fas fa-comments"></i><span> Kkayo</span></div>
            </div>
            <div class="two">
                <div class="back"></div>
                <span>Thank You</span>
            </div>
        </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "connections",
  components: {
  },
};
</script>

<style lang="scss" scoped>
@import '@/scss/base.scss';
@import '@/scss/connection.scss';
</style>
