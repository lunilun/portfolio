<template>
  <div class="projectes">
    <div class="project">
        <span id="top">Project</span>
        <div class="item" v-for="(i,index) in projects" :key="index" data-aos="fade-up">
            <span class="backTxt">Project{{index+1}}</span>
            <template v-if="index%2==0">
              <div class="git" :id="index" @click="git($event)"><img src="@/Image/project/git.png" alt="git"></div>              
              <div class="imgs">
                <img id="bg" :src="i.img" :alt="i.title" width="250px" height="100%">
                <div class="inner">
                    <div class="detail">
                        <div class="title">{{i.title}}</div>
                        <div class="cont" v-for="(j,indexj) in i.spans" :key="indexj">
                            <span>{{j}}</span><br>
                        </div>
                    </div>
                    <div class="uses" v-for="(k,indexk) in i.use" :key="indexk">{{k}}</div>
                </div>
              </div>
            </template>

            <template v-else-if="index%2!=0">
                <div class="git" :id="index" @click="git($event)"><img src="@/Image/project/git.png" alt="git"></div>              
                <div class="imgs">
                    <div class="inner">
                        <div class="detail">
                            <div class="title">{{i.title}}</div>
                            <div class="cont" v-for="(j,indexj) in i.spans" :key="indexj">
                                <span>{{j}}</span><br>
                            </div>
                        </div>
                        <div class="uses" v-for="(k,indexk) in i.use" :key="indexk">{{k}}</div>
                    </div>
                    <img id="bg" :src="i.img" :alt="i.title" width="250px" height="100%">
                </div>
            </template>

        </div>
    </div>
  </div>
</template>

<script>
import AOS from 'aos';
export default {
  name: "projectes",
  components: {
  },
  mounted(){
    AOS.init({
      duration: 1000
    });
  },
    data(){
      return{
        projects:[
            {img:require('@/Image/project/daum.png'), title:"1.imitation Daum", spans:["[Daum 포털 사이트를 비슷하게 만든 웹페이지]","-주요 목적",`◎Componet 분리 및 데이터 바인딩`,`◎기초 CSS`], use:["Vue"]},
            {img:require('@/Image/project/sweet.png'), title:"2.Do you like Sweets?", spans:["[여행 및 디저트를 기록할 수 있는 웹페이지]","-주요 목적","◎ Sass(@mixin ,@include, $..)","◎ Axios를 이용한 Http통신","◎ Vuex의 Getter/mutations"], use:["Vue","Vuex","Sass","Axios","node","Postgresql"]},
            {img:require('@/Image/project/por.png'), title:"3.My Portfolio", spans:["[자기 소개용 포트폴리오 웹페이지]]","-주요 목적","◎ 라이브러리 활용","◎ firebase 호스팅"], use:["Vue","Sass","firebase"]},
        ],
      }
  },
  methods:{
    git(e){
      var i = parseInt(e.currentTarget.id);
      if(i==0) window.open('https://github.com/lunilun/idaum')
      else if(i==1) window.open('https://github.com/lunilun/sweet');
      else window.open('https://github.com/lunilun/portfolio');
    }
  }
};
</script>

<style lang="scss" scoped>
@import '@/scss/base.scss';
@import '@/scss/project.scss';
</style>
