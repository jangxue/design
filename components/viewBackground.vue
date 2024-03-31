<script setup>
import { ref, onMounted, onUnmounted } from "vue";
import { Application } from "@splinetool/runtime";

const specialChars = "-+";
const fullscreenContent = ref(null);
let timerId;
const canvas3d = ref(null);
const generateRandomChars = () => {
  const randomChars = Array.from(
    { length: Math.ceil((window.innerWidth * window.innerHeight) / 100) },
    () => specialChars[Math.floor(Math.random() * specialChars.length)]
  ).join("");
  fullscreenContent.value.textContent = randomChars;
};

onMounted(() => {
  const app = new Application(canvas3d.value);
  app
    .load("https://prod.spline.design/fE-bCphQyWmK0tKW/scene.splinecode")
    .then(() => {
      loading.value = false;
    });
  generateRandomChars();
  timerId = setInterval(generateRandomChars, 300);
  const updateSize = () => {
    fullscreenContent.value.style.fontSize = `${
      Math.min(window.innerWidth, window.innerHeight) / 20
    }px`;
  };
  updateSize();
  window.addEventListener("resize", updateSize);
});

onUnmounted(() => {
  clearInterval(timerId);
});
</script>

<template>
  <main>
    <p class="fullscreen-characters" ref="fullscreenContent"></p>
    <canvas class="logo-bg" ref="canvas3d" id="canvas3d"></canvas>
  </main>
</template>

<style scoped>
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
  width: 60vw;
  z-index: -1;
  position: absolute;
  mix-blend-mode: soft-light;
  right: 0;
  height: 100vh;
}
</style>
