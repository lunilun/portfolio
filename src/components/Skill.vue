<template>
  <div class="mskill">
    <div class="skill">
        <span id="top">Skill</span>
        <div class="skillList">

            <div class="icon" data-aos="fade-up">
                <div class="skills" v-for="(i,index) in skills" :key="index">
                    <img class="im" :id="'skill_img'+index" :src="i.img" :alt="i.name" width="100%" height="100%" @click="ViewItem(index)">
                    <input type="radio" name="selcet" :id="'skill_'+(index)">
                    <label :for="'skill_'+(index)"></label>
                </div>
            </div>

            <div class="infoskill">
                <div class="card" data-aos="fade-up">
                    <div class="wrap">
                        <div class="back">
                            <div class="noClick" v-if="!isSkillClick">
                                <span id="coverTxt">My skill Detail</span><br>
                                <span id="blinkTxt">Click Item</span>
                            </div>
                            <div class="yesClick" v-if="isSkillClick">
                                <div class="target"></div>
                                <div class="using"></div>
                            </div>
                            <div class="mark"><span v-if="isSkillClick"></span></div>
                        </div>
                    </div>
                </div>

                <div class="chart" data-aos="fade-up"><canvas id="draw_chart"></canvas></div>

            </div>
            
        </div>
    </div>
  </div>
</template>

<script>
import Chart from 'chart.js';
import AOS from 'aos';
export default {
  name: "mskill",
  components: {
  },
  mounted(){
    this.createC('draw_chart',this.type,this.data,this.options);
    AOS.init({
      duration: 1000
    });
  },
  data(){
      return{
        isSkillClick:false,
        setUsing:false,
        cnt:-1,
        str:"",
        skills:[
            {img:require('@/Image/skill/html.png'),name:"HTML"},
            {img:require('@/Image/skill/js.png'),name:"JavaScript"},
            {img:require('@/Image/skill/css.png'),name:"css"},
            {img:require('@/Image/skill/scss.png'),name:"scss"},
            {img:require('@/Image/skill/jquery.png'),name:"jquery"},
            {img:require('@/Image/skill/node.png'),name:"node"},
        ],
        skillDetail:[
            {con:["<보유 스킬>","- Html 시맨틱 구조 이해"]},
            {con:["<보유 스킬>","- ES6+ 문법"]},
            {con:["<보유 스킬>","- Grid,Flex 레이아웃","- animation"]},
            {con:["<보유 스킬>","- SCSS 중첩, 변수","- @minin/@include"]},
            {con:["<보유 스킬>","- Selector","- 이벤트 바인딩"]},
            {con:["<보유 스킬>","- node Express","- Rest API"]},
        ],
        colors:[
            'rgba(255,0,0,0.3)','rgba(255,128,0,0.3)','rgba(255,255,0,0.3)','rgba(0,255,0,0.3)','rgba(0,0,255,0.3)','rgba(0,255,255,0.3)'
        ],
        type:'polarArea',
        data:{
            labels:['Html', 'Javascripts', 'Css', 'Sass', 'Jquery','Node'],
            datasets:[{
                label:"alpa",
                data:[30,25,30,30,20,25],
                backgroundColor:[
                    'rgba(255,0,0,0.3)','rgba(255,128,0,0.3)','rgba(255,255,0,0.3)','rgba(0,255,0,0.3)','rgba(0,0,255,0.3)','rgba(0,255,255,0.3)'
                ],
                max:100,
            }]
        },
        options:{
            scale: {
            angleLines: {
                display: false
            },
            ticks: {
                beginAtZero: true,
                min: 0,
                max: 100,
                stepSize: 10
            },
            pointLabels: {
                fontSize: 18,
                fontColor: "green"
            }
            },
        }
      }
  },
  methods:{
    ViewItem(i){
        if(!this.isSkillClick){
           this.turnOnOff();
        }
        
        const eleRadio = document.getElementById(`skill_${i}`);
        const eleIcon = document.getElementById(`skill_img${i}`);
        const parent = eleIcon.parentNode;
        eleRadio.checked=true;
        for(var k=0;k<this.skills.length;k++){
            document.getElementById(`skill_img${k}`).style.transform="scale(1)";
            document.getElementById(`skill_img${k}`).style.transition="all .9s";
            document.getElementById(`skill_img${k}`).parentNode.style.border="none";
            document.getElementById(`skill_img${k}`).parentNode.style.boxShadow="1px 1px 5px rgba($color: #000000, $alpha: .5)";
        }
        
        if(eleRadio.checked){
            parent.style.border="2px solid black"
            eleIcon.style.transform="scale(.8)"
            eleIcon.style.transition="all .9s"    
        }
        this.cnt=i;
        setTimeout(() => {
            const eleT = document.getElementsByClassName("target");
            const eleU = document.getElementsByClassName("using");
            const eleMark = document.getElementsByClassName("mark");

            this.setOff(eleT[0],eleU[0]);
            eleMark[0].style.background=this.colors[i];
            eleMark[0].style.transition="all .8s";
            setTimeout(() => {
                this.setOpa(eleT[0]);
                eleT[0].innerHTML=this.skills[i].name;
            }, 650);

            setTimeout(() => {
                this.str="";
                this.setOpa(eleU[0]);
                for(var num=0;num<this.skillDetail[i].con.length;num++){
                    this.str+=`<span style="margin-left:15px">${this.skillDetail[i].con[num]}</span><br>\n`
                }
                eleU[0].innerHTML=this.str;
            }, 1000);
        }, 600);
        
    },
    setOpa(ele){
    ele.style.opacity="1";
    ele.style.transition="all .5s";
    },
    setOff(el1,el3){
        el1.style.opacity="0";
        el3.style.opacity="0";
    },
    turnOnOff(){
        const eleYesClick = document.getElementsByClassName('yesClick');
        setTimeout(() => {
            this.isSkillClick = true;
        }, 500);

        setTimeout(() => {
            eleYesClick[0].style.opacity='1';
            eleYesClick[0].style.transition= 'all 1.5s';
        }, 550);
    },
    createC(charid, type,data,option){
      var ctx = document.getElementById(charid).getContext("2d");
      new Chart(ctx,{
        type:type,
        data:data,
        options:option,
      });
    }
  }
};
</script>

<style lang="scss" scoped>
@import '@/scss/base.scss';
@import '@/scss/skill.scss';
</style>
