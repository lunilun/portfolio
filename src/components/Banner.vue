<template>
  <div class="banner">
    <div class="title">My Portfolio</div>
    <div class="back">
         <vue-typer id="vue-typer"
            :text='["Front-end Developer?","Back-end Developer?","Full-stack Developer!!"]'
            :repeat='Infinity'
            :shuffle='false'
            initial-action='typing'
            :pre-type-delay='70'
            :type-delay='120'
            :pre-erase-delay='2500'
            :erase-delay='250'
            :erase-on-complete='false'
        ></vue-typer>
        <div class="clickMotion">
            <img src="@/Image/searchEffect.png" alt="검색 이미지" width="80px" height="80px">
        </div>
    </div>

    <div class="down" @click="goDown">
        <div class="arrow">˅</div>
        <div class="arrow">˅</div>
    </div>
  </div>
</template>

<script>
export default {
  name: "banner",
  components: {
  },
  data(){
      return{
          isMenu:false,
      }
  },
  mounted(){
  },
  methods:{
    goDown(){
        // var location = document.querySelector(".start").scrollHeight;
        var loc = document.querySelector(".banner").offsetHeight;
        window.scrollTo({top:loc, behavior:'smooth'});
    },
    sendClickValue(ev){
      try{   
        this.$emit('send',ev.target.innerText);
      }catch(e){
        console.log(e);
      }
    },
  }
};
</script>

<style lang="scss" scoped>
@import '@/scss/base.scss';
@import '@/scss/banner.scss';
</style>
