<template>
    <transition-group name="fade" mode="out-in" tag="div">
      <div class="slideImage" :style="setBackgroundImage" :key="image.id">

      </div>
    </transition-group>
</template>

<script>
  export default{
    props:["image"],
    computed:{
      setBackgroundImage(){
        return{backgroundImage : "url("+this.image.url+")"}
      }
    }
  }
</script>

<style>
#slides{

}
 .slideImage{
  height:500px;
  width:100%;
  background-position:center;
  background-repeat:no-repeat;
  background-size:cover;
  /*background-image:url("/images/ddochi.jpg")*/
}

.fade-enter-active{
  animation-name:fadeEnter;
  animation-duration:1s;
  animation-iteration-count:1;
}
.fade-move{
  transition: all 1s;
}
.fade-leave-active{
  animation-name:fadeLeave;
  animation-duration:1s;
  animation-iteration-count:1;
  position:absolute;
}
@keyframes fadeEnter{
  from{
    opacity:0;
  }
  to{
    opacity:1;
  }
}
@keyframes fadeLeave{
  from{
    opacity:1;
  }
  to{
    opacity:0;
  }
}
</style>
