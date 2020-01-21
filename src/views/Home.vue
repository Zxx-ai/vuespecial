<template>
  <div class="starry">
    <div v-for="(item,index) in starConunt" :key="index" class="star" ref="star"></div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      starConunt: 800, //星星数量
      distance: 800 //问题
    };
  },
  mounted(){

let _this=this

let starry=_this.$refs.star

console.log(starry)

starry.forEach(item =>{
var speed=0.2 + (Math.random() * 1);
var thisDist=_this.distance + (Math.random()* 300 );
item.style.transformOrigin=`0 0 ${thisDist}px`;
item.style.transform=`translate3d(0,0,-${thisDist}px) rotateY(${(Math.random()*360)}deg) rotateX(${(Math.random() * -50)}deg) scale(${speed},${speed})`;


 })


  }
};
</script>

<style lang="less" scoped>
//动画
@keyframes rotate{
  0% {
    transform: perspective(400px) rotateZ(20deg) rotateX(-40deg) rotateY(0);
  }

  100% {
    transform: perspective(400px) rotateZ(20deg) rotateX(-40deg) rotateY(-360deg);
  }
}

.starry{
transform: perspective(500px);
transform-style: preserve-3d;
position: absolute;
perspective-origin: 50% 100%;
left: 50%;
animation: rotate 90s infinite linear;
bottom: 0;

}



.star{
width: 2px;
height: 2px;
background: #f7f7b8;
position: absolute;
top: 0;
left: 0;
backface-visibility: hidden;

}
</style>