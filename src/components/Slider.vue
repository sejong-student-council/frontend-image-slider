<template>
<div class="container">
  <div id="Slider">
    <div class="arrowLeft" @click="arrowLeft"></div>
    <Slides :image="images[chosenImage]"></Slides>
    <div class="arrowRight" @click="arrowRight"></div>
    <div class="dots">
      <div @click="dots(image.id)" v-for="image in images" :key="image.id"></div>
    </div>
  </div>
</div>
</template>

<script>
import Slides from './Slides.vue'
export default{
  components:{
    'Slides':Slides
  },
  data(){
    return{
      images : [
        {
          id:"0",
          url:"/images/ddochi.jpg",
          title:"1"
        },
        {
          id:"1",
          url:"/images/ddochi2.jpg",
          title:"2"
        },
        {
          id:"2",
          url:"/images/ddochi3.jpg",
          title:"3"
        }
      ],
      chosenImage : 0,
      intervalObjact : null
    }
  },
  methods:{
    dots(id){
      this.chosenImage = id;
      clearInterval(this.intervalObjact);
      var self=this;/*call back*/
      this.intervalObjact = setInterval(()=>{
        self.move();
      },4000);
    },
    arrowLeft(){
      clearInterval(this.intervalObjact);
      this.moveLeft();
      var self=this;/*call back*/
      this.intervalObjact = setInterval(()=>{
        self.moveLeft();
      },4000);
    },
    arrowRight(){
      clearInterval(this.intervalObjact);
      this.moveRight();
      var self=this;/*call back*/
      this.intervalObjact = setInterval(()=>{
        self.moveRight();
      },4000);
    },
    moveLeft(){
      var flag = this.chosenImage;
      flag--;
      if(flag<0){
        flag=(this.images.length-1);
      }
      this.chosenImage=flag;
    },
    moveRight(){
      var flag = this.chosenImage;
      flag++;
      if(flag>=this.images.length){
        flag=0;
      }
      this.chosenImage=flag;
    },
    move(){
      var flag = this.chosenImage;
      flag++;
      if(flag>=this.images.length){
        flag=0;
      }
      this.chosenImage=flag;
    }
  },
  created(){
    var self=this;/*call back*/
    this.intervalObjact = setInterval(()=>{
      self.move();
    },4000);
  }
}
</script>

<style>
#Slider{
  position:relative;
}
#Slider .arrowLeft,#Slider .arrowRight{
  position:absolute;
  top: 50%;
  border:20px solid transparent;
}
#Slider .arrowLeft{
  border-right-color:red;
  z-index:1;
}
#Slider .arrowRight{
  right:0;
  border-left-color:red;
}
#Slider .dots{
  position:absolute;
  bottom:0;
  left:50%;
  transform:translate(-50%, -50%);
}
#Slider .dots div{
  height:20px;
  width:20px;
  margin-right:10px;
  display: inline-block;
  background-color:gray;
  border-radius:100%;
}
</style>
