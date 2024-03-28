<template>
  <div class="scroll-container">
    <ul class="scroll-text" :style="{ animationDuration: duration + 's' }">
      <li v-for="(item, index) in texts" :key="index">{{ item }}</li>
    </ul>
  </div>
</template>

<script setup>
import { ref, defineProps, onMounted } from "vue";

const props = defineProps({
    text: {
    type: String,
    default: "Jiangxue Lab,jiangxue Team,Web3 Acg lab,Web3in Tech,Dexnav,sifone,NPO NETWORK,jointNOW,IENP,CASSI,Wet Spring Alert,spec,seti@home web3,crg fps,Asteroid,splash,Nicho,ienn,hucsrc,zhongshan"
  }
});
const originalText = props.text;

let arr = originalText.split(",");
const texts = ref(arr);

onMounted(() => {
  setInterval(() => {
    for (let i = arr.length - 1; i > 0; i--) {
      const j = Math.floor(Math.random() * i);
      const temp = arr[i];
      arr.splice(i, 1, arr[j]);
      arr.splice(j, 1, temp);
    }
    texts.value = [...arr];
  }, 1000);
});

const duration = ref(10);
</script>

<style scoped>
.scroll-container {
  overflow: hidden;
  height: 50px;
  width: min-content;
}

.scroll-text {
  white-space: nowrap;
  color: rgb(255, 255, 255);
  animation: scroll linear infinite;
  width: fit-content;
  display: table-row-group;
}
ul li {
  padding: 0;
  margin: 0;
  list-style-type: none;
  text-transform: uppercase;
}
</style>
