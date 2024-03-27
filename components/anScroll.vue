<template>
  <div class="scroll-container">
    <ul class="scroll-text" :style="{ animationDuration: duration + 's' }">
      <li v-for="(item, index) in texts" :key="index">{{ item }}</li>
    </ul>
  </div>
</template>

<script setup>
import { ref, computed } from "vue";

const originalText =
  "OCEAN,SIPHER,SHRAPNEL,SHOWTIME,SENSE FINANCE,SAFFRON FINANCE,SADDLE,RIBBON FINANCE,REVEL,QUANTSTAMP,QUADRATA,POOLTOGETHER,POLYGON,PLEASRDAO,PARTYDAO,PARCL,PARADIGM";

const texts = computed(() => originalText.split(","));

const duration = ref(10); 
</script>

<style scoped>
.scroll-container {
  overflow: hidden;
  height: 50px;
  border: 1px solid red;
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
}
@keyframes scroll {
  0% {
    transform: translateY(0);
  }
  100% {
    transform: translateY(-100%);
  }
}
</style>
