<script setup>
const props = defineProps(["lanesData"]);
</script>
<template>
  <div v-for="horses in lanesData" class="lanes">
   
    <i
      :style="{ left: horses.distance + 'px' }"
      :class="horses.name"
      class="fa-solid fa-horse"
    ></i>
    <p class="start__text">start</p>
    <div class="start"></div>
    
    <div class="finish"></div>
    <p class="finish__text">finish</p>
  </div>
</template>
<style scoped>
.lanes {
  background-color: green;
  margin: 10px 0px;
  height: 35px;
}
.fa-horse {
  font-size: 20px;
  margin-top: 7px;
  position: relative;
}
.start {
      width: 3px; 
      height: 34px;
      float: left;
      background-color: red; 
      margin-left: 90px;
    }
.finish {
      width: 3px; 
      height: 34px;
      float: right;
      background-color: red; 
      margin-right: 50px;
    }    
.start__text {
      margin-left: 50px;
      margin-top: -20px;
      position: absolute;
      color: black;
    }
.finish__text {
     
      float: right;
      margin-top: 7px;
      color: black;
    }    

.horse1 {
  color: red;
}
.horse2 {
  color: black;
}
.horse3 {
  color: yellow;
}
.horse4 {
  color: blue;
}
.horse5 {
  color: white;
}
.horse6 {
  color: orange;
}
.horse7 {
  color: purple;
}
.horse8 {
  color: hotpink;
}
</style>
