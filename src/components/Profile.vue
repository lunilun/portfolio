<template>
  <div class="profiles">
    <div class="profile">
        <span id="top">Profile</span>
        <div class="inner">
                <div class="mainImgCover">
                <div class="mainImg">
                    <img src="@/Image/me.jpg" alt="프로필 이미지" width="300px" height="300px">
                </div>
            </div>
            <div class="contents">
                <div class="tag2">
                    <span>소개</span>
                    <div id="temp">
                        안녕하세요. Full-stack 개발자를 목표로 노력하는 초보 개발자 강다빈입니다.<br>
                        Vuforia 프로젝트에서 서버 연동 및 웹어플리케이션 개발 보조를 맡으면서
                        '좀 더 잘 만들어보고 싶다'라는 생각을 가지게 되어 공부를 시작하게 되었습니다.
                        현재 vue를 주로 공부하는 중이며, 연습용 프로젝트에 따라서 node.js 
                        Postgresql, firebase등 다양하게 공부하고 있습니다.
                    </div>
                </div>
            </div>
        </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "profiles",
  components: {
  },
};
</script>

<style lang="scss" scoped>
@import '@/scss/base.scss';
@import '@/scss/profile.scss';
</style>
