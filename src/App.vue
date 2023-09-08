<template>
  <div class="head_1">
    เป่ายิงฉุบBot Vs Bot
  </div>
  <br>
  <div class="text_bot">
    Bot 1 เลือก {{ pic[sum_1].name }}
    <div v-if="sum_1 === 1">
      <img src="https://tse1.mm.bing.net/th?id=OIP.Zh_2aYAWbvQHF5dIqXOZggAAAA&pid=Api&P=0&h=180">
    </div>
    <div v-if="sum_1 === 2">
      <img src="https://tse2.mm.bing.net/th?id=OIP.gvG03wNwmRqQ0letJLLaxgAAAA&pid=Api&P=0&h=180">
    </div>
    <div v-if="sum_1 === 3">
      <img src="https://tse4.mm.bing.net/th?id=OIP.QS5YIu-CtrSBFE3spsq4sAHaEc&pid=Api&P=0&h=180">
    </div>
    <div v-if="sum_1 === 4">
      <img src="https://tse4.mm.bing.net/th?id=OIP.Zq7jxyLLNX-L8PMJBhZsmwHaE5&pid=Api&P=0&h=180">
    </div>
  </div>
  <div class="text_bot">
    Bot 2 เลือก {{ pic[sum_2].name }}
    <div v-if="sum_2 === 1">
      <img src="https://tse1.mm.bing.net/th?id=OIP.Zh_2aYAWbvQHF5dIqXOZggAAAA&pid=Api&P=0&h=180">
    </div>
    <div v-if="sum_2 === 2">
      <img src="https://tse2.mm.bing.net/th?id=OIP.gvG03wNwmRqQ0letJLLaxgAAAA&pid=Api&P=0&h=180">
    </div>
    <div v-if="sum_2 === 3">
      <img src="https://tse4.mm.bing.net/th?id=OIP.QS5YIu-CtrSBFE3spsq4sAHaEc&pid=Api&P=0&h=180">
    </div>
    <div v-if="sum_2 === 4">
      <img src="https://tse4.mm.bing.net/th?id=OIP.Zq7jxyLLNX-L8PMJBhZsmwHaE5&pid=Api&P=0&h=180">
    </div>
  </div>
  <br>
  <div>    
    <label class="text">คะแนน</label><br>
    <label class="text">Bot 1 ชนะ {{ bot1Score }}</label>
    <br>
    <label class="text">Bot 2 ชนะ {{ bot2Score }}</label>
  </div>
  <div>
    <button @click="randomChoice" class="buto" :disabled="isDisabled">เริ่มสู้</button>
    <button @click="resetGame" class="buto">รีเกม</button>
  </div>
</template>

<script setup>
import { ref } from "vue";

const pic = ref([
  { name: "รอเริ่ม" },
  { name: "ค้อน" },
  { name: "กรรไกร" },
  { name: "กระดาษ" },
  { name: "หัวใจ" }
]);
const sum_1 = ref(0);
const sum_2 = ref(0);

const bot1Score = ref(0);
const bot2Score = ref(0);

const isDisabled = ref(false);

function randomChoice() {
  // สุ่มค่าสำหรับ Bot 1 และ Bot 2
  sum_1.value = Math.floor(Math.random() * 4) + 1;
  sum_2.value = Math.floor(Math.random() * 4) + 1;

  // คำนวณคะแนน
  if (sum_1.value== 1){
    if (sum_2.value == 3 || sum_2.value == 4){
      bot2Score.value+=1;
    }
    if (sum_2.value == 2){
      bot1Score.value+=1;
    }
  }
  if (sum_1.value == 2){
    if (sum_2.value == 1 || sum_2.value == 4){
      bot2Score.value+=1;
    }
    if (sum_2.value == 3){
      bot1Score.value+=1;
    }
  }
  if (sum_1.value == 3){
    if (sum_2.value == 1 || sum_2.value == 4){
      bot2Score.value+=1;
    }
    if (sum_2.value == 1){
      bot1Score.value+=1;
    }
  }
  if (sum_1.value == 4){
    if (sum_2.value == 1 || sum_2.value == 2 || sum_2.value == 3){
      bot1Score.value+=1;
    }
  }
}

function resetGame() {
  // รีเซ็ตคะแนนและการเลือกของ Bot 1 และ Bot 2
  bot1Score.value = 0;
  bot2Score.value = 0;
  sum_1.value = 0;
  sum_2.value = 0;
  isDisabled.value = false; // เปิดให้ปุ่ม "เริ่มสู้" ใช้งาน
}
</script>

<style>
* {
  background-color: gray;
}
.head_1 {
  color: black;
  background-color: white;
  font-size: 60px;
  display: flex;
  justify-content: center;
  align-items: center;
}
.text_bot {
  font-size: 36px;
  color: black;
}
.buto{
  font-size: 36px;
  background-color: white;
  margin: 10%;
}
.text{
  font-size: 30px;
  color: black;
}
</style>
