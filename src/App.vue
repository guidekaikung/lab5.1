<template>
  <div>
    <div id="app">
      <div class="player">
        <img :src="player1Image" alt="Player 1" />
      </div>
      <div class="player">
        <img :src="player2Image" alt="Player 2" />
      </div>
      <div class="content-container">
        <p>Player 1: {{ player1Score }}</p>
        <p>bot: {{ player2Score }}</p>
        <button @click="playGame">เป่ายิ๊งฉุบ</button>
        <button @click="startNewGame">เริ่มใหม่</button>
      </div>
    </div>
  </div>
</template>


<script setup>
import { ref } from 'vue';

const images = [
  { url: 'https://png.pngtree.com/png-clipart/20190904/original/pngtree-hammer-illustration-hammer-png-image_4484925.jpg', value: 1 },
  { url: 'https://www.shutterstock.com/image-vector/scissors-cartoon-vector-illustration-pair-250nw-1291096546.jpg', value: 2 },
  { url: 'https://w7.pngwing.com/pngs/618/28/png-transparent-paper-paper-clip-torn-lined-paper-paper-sheet-note-scrapbooking-scrapbook-wrinkled-paper-creased-paper.png', value: 3 },
  { url: 'https://i.pinimg.com/736x/fc/ce/43/fcce433d815cdb327bf242bb5221a029.jpg', value: 4 },
];

const player1Image = ref('');
const player2Image = ref('');
const player1Score = ref(0);
const player2Score = ref(0);

function getRandomNumber() {
  return Math.floor(Math.random() * images.length);
}

function playGame() {
  const player1Index = getRandomNumber();
  const player2Index = getRandomNumber();

  player1Image.value = images[player1Index].url;
  player2Image.value = images[player2Index].url;

  if (images[player1Index].value > images[player2Index].value) {
    player1Score.value += 1;
  } else if (images[player1Index].value < images[player2Index].value) {
    player2Score.value += 1;
  }
}

function startNewGame() {
  player1Score.value = 0;
  player2Score.value = 0;
  player1Image.value = '';
  player2Image.value = '';
}
</script>

<style scoped>
#app {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh; 
  background-color: rgb(197, 238, 234); 
}

.player {
  text-align: center;
  margin: 0 20px;
}
.player img {
  width: 200px; 
  height: 200px; 
}
</style>
