<template>
  <div class="sidebar">
      <button id="gotop">
        <div class="inner">Top</div>
        <div class="cpoint" v-show="isCpoint[0]"></div>
      </button>
      <button id="gointro" @click="sendClickValue($event)">
        <div class="inner">introduce</div>
        <div class="cpoint" v-show="isCpoint[1]"></div>
      </button> 
      <button id="goskill" @click="sendClickValue($event)">
        <div class="inner">skill</div>
        <div class="cpoint" v-show="isCpoint[2]"></div>
      </button>
      <button id="goproject"  @click="sendClickValue($event)">
        <div class="inner">project</div>
        <div class="cpoint" v-show="isCpoint[3]"></div>
      </button>
      <button id="gobottom">
        <div class="inner">connect</div>
        <div class="cpoint" v-show="isCpoint[4]"></div>
      </button>
  </div>
</template>

<script>
export default {
  name: "sidebar",
  components: {
  },
  data(){
    return{
      isCpoint:[false,false,false,false,false],
    }
  },
  mounted(){
    document.getElementById("gotop").addEventListener('click', function(){
      window.scrollTo({top:0, behavior:'smooth'});
    });

    document.getElementById("gobottom").addEventListener('click', function(){
      window.scrollTo({top:document.body.scrollHeight, behavior:'smooth'});
    });

    setInterval(() => {
      if(window.pageYOffset<432) this.$set(this.isCpoint, 0, true);
      else this.$set(this.isCpoint, 0, false);

      if(window.pageYOffset>=432 && window.pageYOffset<=840.79) this.isCpoint[1]=true;
      else this.isCpoint[1]=false;

      if(window.pageYOffset>840.79 && window.pageYOffset<1510.4) this.isCpoint[2]=true;
      else this.isCpoint[2]=false;
      
      if(window.pageYOffset>=1510.4 && window.pageYOffset<2292) this.isCpoint[3]=true;
      else this.isCpoint[3]=false;

      if(window.pageYOffset>=2292) this.isCpoint[4]=true;
      else this.isCpoint[4]=false;
    }, 100);
  },
  methods:{
    sendClickValue(ev){
      try{
        this.$emit('send',ev.target.childNodes[0].innerText);
      }catch(e){
        console.log();
      }
    }
  },
};
</script>

<style lang="scss" scoped>
@import '@/scss/base.scss';
@import '@/scss/sidebar.scss';
</style>
