<template>
  <div class="pchome">
    <Load id="load" v-if="!isLoad"/>
    <div class="wrap">
        <Banner id="banner" @send="moveScroll_sizing"/>
        <div class="body" v-if="isLoad">
          <Profile id="introduce" data-aos="fade-up"/>
          <Mskill id="skill"/>
          <Mproject id="project"/>
          <Connection data-aos="fade-up"/>
        </div>
        <div class="footer" v-if="isLoad">
            <div>Copyright 2022</div>
            <div>Present by Hosikawa Ayumu🌸</div>
        </div>
    </div>
    <Sidebar @send="moveScroll"/>
  </div>
</template>

<script>
import Profile from "@/components/Profile.vue"
import Mskill from "@/components/Skill.vue"
import Mproject from "@/components/Projectes.vue"
import Connection from "@/components/Connection.vue"

import Banner from "@/components/Banner.vue"
import Sidebar from "@/components/sidebar.vue"
import Load from "@/components/Loading.vue"

import 'animate.css';
import AOS from 'aos';

export default {
  name: "pchome",
  components: {
    Profile,
    Mskill,
    Mproject,
    Connection,
    Banner,
    Sidebar,
    Load,
  },
  created(){
    window.onload = function() {
    setTimeout (function () {
        scrollTo(0,0);
      }, 100);
    },
    
    setTimeout(() => {
      document.getElementById("load").style.opacity="0";
      document.getElementById("load").style.transition="all 1s";
      setTimeout(() => {
        this.isLoad=true;
      }, 800);
    },1800);
    
    AOS.init({
      duration: 1000
    });
  },
  data(){
    return{
      isLoad:false,
    }
  },
  mounted(){
  },
  methods: {
    moveScroll(val){
      if(val=="introduce"){
        var loc = document.querySelector("#banner").offsetHeight;
        window.scrollTo({top:loc, behavior:'smooth'});
      }
      else document.querySelector(`#${val}`).scrollIntoView({behavior : 'smooth'});
    },
    moveScroll_sizing(val){
      if(val=="top"){
        window.scrollTo({top:0, behavior:'smooth'});
      }else if(val=="connect"){
        document.querySelector(`.footer`).scrollIntoView({behavior : 'smooth'});
      }
      else {
        document.querySelector(`#${val}`).scrollIntoView({behavior : 'smooth'});
      }
    },
  },
};
</script>

<style lang="scss" scoped>
@import '@/scss/base.scss';
@import '@/scss/home.scss';
</style>
