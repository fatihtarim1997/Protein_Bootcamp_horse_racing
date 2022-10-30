<script setup>
import { ref } from "vue";

const props = defineProps(["countDownTime","countDownToogle"]);

</script>
<template>
 
  <teleport to="body">
    <div class="modal" v-if="props.countDownToogle">
      <h2 class="modal__text">{{ props.countDownTime }}</h2>
    </div>
  </teleport>
</template>
<style scoped>
.modal {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(247, 7, 7, 0.5);
  display: flex;
  justify-content: center;
  align-items: center;
}
.modal__text {
  font-size: 1000px;
  color: white;
}
</style>
