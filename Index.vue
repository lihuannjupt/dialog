<template>  
  <div class="btn" v-if="show"> 
      <div class="mask" @click="shownone"></div>
      <div class="isdialog">
        <transition name="dialog">
            <div class="dialog" v-bind:class="{in:isIn,out: isOut}">
                  <div class="con">
                      <div class="title" v-if="data.title">{{data.title}}</div>
                      <div class="sub-title" v-if="data.subtitle">{{data.subtitle}}</div>
                      <div class="text" v-if="data.text">{{data.text}}</div>
                  </div>
                  <div class="onebtn" id="1" v-if="data.button.length==1" @click="function1" >{{data.button[0]}}</div>
                  <div class="twobtn" v-if="data.button.length==2" @click="function1">
                      <div id="1" class="btnleft" >{{data.button[0]}}</div>
                      <div id="2" class="btnright" >{{data.button[1]}}</div>
                  </div>  
             </div>          
       </transition>
     </div>  
  </div>
</template>

<script>
export default {
  name: 'Dialog',
  data(){
    return {
      show:true,
      isIn:true,
      isOut:false
    }
  },  
  props: {
    data: {
      type: Object
    }
  },

  methods: {
    function1(e) {
      this.isIn=false;
      this.isOut=true      
      let index=e.toElement.id  
      window.setTimeout(()=>{this.show=false},200)
      this.$emit('function1',{'index':index});
    },
    shownone(){
      this.isIn=false;
      this.isOut=true  
      window.setTimeout(()=>{this.show=false},200)   
    },
  }
  
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

.mask{
  position: fixed;
  top:0px;
  left: 0px;
  right: 0px;
  bottom: 0px;
  background: #000;
  opacity: 0.15;
  animation: opacity 0.15s;
}
.isdialog{
  position: absolute;
  top:50%;
  left: 50%;
  transform: translate(-50%,-50%);
  -webkit-transform: translate(-50%,-50%);
 
}
.dialog{
  padding: 5px ;
  width: 282px;
  background-color: #fff; 
  /* animation: bounce-in 0.15s; */
}
.in  {
  -webkit-animation: bounce-in 0.15s;
  animation: bounce-in 0.15s;
}
.out  {
  animation: bounce-out 0.2s ;
   -webkit-animation: bounce-out 0.2s;
}
@keyframes bounce-out{
  0% {
    transform: scale(1);
  }
  100% {
    transform: scale(0.7);
  }
}
@keyframes bounce-in{
  0% {
    transform: scale(0.7);
  }
  100% {
    transform: scale(1);
  }
}
@keyframes opacity{
  0% {
    opacity: 0;
  }
  100% {
    opacity: 0.15;
  }
}
.con{
  padding: 5px 15px 5px 15px;
}
.title{
  font-family: PingFangSC-Medium;
  font-size: 19px;
  color: #292D33;
  line-height: 17px;
  font-weight: bold;
  padding: 10px 0px 5px 0px;
}
.sub-title{
    font-family: PingFangSC-Regular;
    font-size: 17px;
    color: #333333;
    letter-spacing: 0;
    line-height: 17px;
    padding: 10px 0px 5px 0px;  
}
.text{
  font-size: 14px;
  color: #292D33;
  line-height: 18px;
  padding: 10px 0px 5px 0px;
  text-align:justify;
  letter-spacing: 0;
}
.onebtn{
  width: 262px;

  height: 33px;
  overflow: hidden;
  background-color:#E6454A; 
  font-size: 17px;
  color: #fff;
  /* padding-top: 14px; */
  position: relative;
  padding-top: 7px;
  margin: 10px 10px 10px 10px;
  text-align: center;
}
/* .onebtn:active{
  background-color: #F5F7FA;
} */
.twobtn{
  width: 262px;
  height: 40px;
  margin: 10px;
  position: relative;
}


.btnleft{
  display: inline-block;
  width: 250px;
  height: 66px;
  font-size: 34px;
  background-color:#fff ;
  color: #000;
  padding-top: 14px;
  border: 1px solid #BCC5D1;
  position: relative;
  transform: scale(0.5) ;
   -webkit-transform-origin: 0 0;
transform-origin: 0 0; 
}
.btnleft:active{
   background-color: #F5F7FA;
}

.btnright{
  display: inline-block;
  width: 126px;
  height: 33px;
  padding-top: 7px;
  font-size: 17px;
  background-color:#E7454A ;
  color: #fff;
  top:0px;
  right: 0px;
  position: absolute;
}
.btnright:active{
  background-color: #F5F7FA;
}
</style>

