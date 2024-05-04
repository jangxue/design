<script setup>
import { ref, onMounted, onUnmounted, nextTick } from "vue";

const specialChars = "-+";
const fullscreenContent = ref(null);
let timerId;
const generateRandomChars = () => {
  const randomChars = Array.from(
    { length: Math.ceil((window.innerWidth * window.innerHeight) / 80) },
    () => specialChars[Math.floor(Math.random() * specialChars.length)]
  ).join("");
  fullscreenContent.value.textContent = randomChars;
};

onMounted(async () => {
  generateRandomChars();
  timerId = setInterval(generateRandomChars, 300);
  const updateSize = () => {
    fullscreenContent.value.style.fontSize = `${
      Math.min(window.innerWidth, window.innerHeight) / 20
    }px`;
  };
  updateSize();
  window.addEventListener("resize", updateSize);

  await nextTick();
  const loadDiv = document.querySelector('.load');
  if (loadDiv) loadDiv.style.display = 'none';
});

onUnmounted(() => {
  clearInterval(timerId);
});
</script>

<template>
  <div class="load"></div>
  <main>
    <p class="fullscreen-characters" ref="fullscreenContent"></p>
    <img class="logo-bg" src="/img/logo/background.gif" alt="background-img" />
  </main>
</template>

<style scoped>
.load {
    position: absolute;
    background: rgb(0, 0, 0);
    width: 100%;
    height: 100%;
    z-index: 3;
}
/* data */
.fullscreen-characters {
  text-align: center;
  position: absolute;
  color: rgb(255, 255, 255);
  font-size: small !important;
  height: 100vh;
  font-weight: bold;
  overflow: hidden;
  display: block;
  z-index: 1;
  mix-blend-mode: color-burn;
  background: #000;
  margin: 0;
}

/* logo bg */
.logo-bg {
  width: 130vw;
  z-index: -1;
  position: absolute;
  mix-blend-mode: soft-light;
  right: 0;
  top: -3rem;
  height: 100vh;
}
</style>
