<script setup>
import { watch, computed, ref } from "vue";
import _ from "lodash";

const props = defineProps(["leaderData", "gameFinished"]);

// Atların aktif olarak sıralanması
const raceList= computed(() => {
  return _.orderBy(props.leaderData, ["distance"], ["desc"]);
}); 

</script>
<template>
  <div class="leader__board">
    <ul class="horse__list">
      <li v-for="horses in raceList" :class="horses.name" class="horses">
        {{ horses.name }} 
      </li>
    </ul>
  </div>
</template>
<style scoped>
.horse__list {
  list-style: none;
  padding: 0;
  margin: 0;
  display: flex;
  flex-direction: column;
  align-items: center;
}
.horses {
  font-size: 20px;
  margin: 5px 0px;
  padding: 10px;
  border-radius: 5px;
  background-color: #f0f0f0;
  width: 200px;
  transition: 0.5s;
}
.horse1 {
  background-color: red;
}
.horse2 {
  background-color: black;
}
.horse3 {
  background-color: yellow;
}
.horse4 {
  background-color: blue;
}
.horse5 {
  background-color: white;
}
.horse6 {
  background-color: orange;
}
.horse7 {
  background-color: purple;
}
.horse8 {
  background-color: hotpink;
}
</style>
