<script setup>
import { ref, computed, watch } from "vue";
import Lanes from "./components/Lanes.vue";
import LeaderBoard from "./components/LeaderBoard.vue";
import Countdown from "./components/Countdown.vue";

const countDownTime = ref(4);
const countDownToogle = ref(false);
const restartGameToogle = ref(false);
var gameTimer;
const horses = ref([
  {
    id: 1,
    name: "horse1",
    distance: -581,
    finished: false,
  },
  {
    id: 2,
    name: "horse2",
    distance: -581,
    finished: false,
  },
  {
    id: 3,
    name: "horse3",
    distance: -581,
    finished: false,
  },
  {
    id: 4,
    name: "horse4",
    distance: -581,
    finished: false,
  },
  {
    id: 5,
    name: "horse5",
    distance: -581,
    finished: false,
  },
  {
    id: 6,
    name: "horse6",
    distance: -581,
    finished: false,
  },
  {
    id: 7,
    name: "horse7",
    distance: -581,
    finished: false,
  },
  {
    id: 8,
    name: "horse8",
    distance: -581,
    finished: false,
  },
]);

// Tüm atların bitiş çizgisine ulaşmasının kontrolü
const gameFinished = computed(() => {
  return horses.value.filter((horse) => horse.finished).length === 8;
});

// Başlangıç animasyonun başlatılması
const countDownTimer = () => {
  gameTimer = setInterval(countDownHandler, 1000);
};
// Başlangıç animasyonunun kontrolü
const countDownHandler = () => {
  countDownToogle.value = true;
  countDownTime.value--;
  if (countDownTime.value < 0) {
    countDownToogle.value = false;
  }
};
// Atların birim zamanda alacakları rasgele mesafe
const horseDistance = () => {
  horses.value.forEach((horse) => {
    if (!horse.finished) {
      horse.distance += Math.floor(Math.random() * 5);
    }
  });
};
// Tekil olarak atların bitiş çizgisine ulaşmasının kontrolü
const raceWatch = watch(() => {
  horses.value.forEach((horse) => {
    if (horse.distance >= 533) {
      horse.finished = true;
    }
  });
});
// Tüm atların bitiş çizgisine ulaşmaştığında restart buttonunun gösterilmesi
const restartGameHandler = watch(() => {
  if (gameFinished.value) {
    clearInterval(gameTimer);
    restartGameToogle.value = true;
  }
});
// Yarışın tekrardan başlatılması
const restartGame = () => {
  restartGameToogle.value = true;
  horses.value.forEach((horse) => {
    horse.distance = -581;
    horse.finished = false;
  });
  countDownTime.value = 4;
  countDownToogle.value = false;
  restartGameToogle.value = false;
  startGame();
};
// Yarışın başlatılması
const startGame = () => {
  countDownTimer();
  setTimeout(function () {
    gameTimer = setInterval(horseDistance, 30);
  }, 4100);
};
</script>

<template>
  <button @click="startGame">Start Race</button>
  <button v-if="restartGameToogle" @click="restartGame">Restart Game</button>

  <div class="canvas">
    <Lanes :lanesData="horses"></Lanes>
    <LeaderBoard
      :leaderData="horses"
      :gameFinished="gameFinished"
    ></LeaderBoard>
  </div>
  <Countdown
    :countDownTime="countDownTime"
    :countDownToogle="countDownToogle"
  />
</template>

<style scoped>
.canvas {
  background-color: white;
  width: 1200px;

  flex-direction: column;
  display: flex;
}
</style>
