<script setup>
import { gsap } from "gsap";
import { ScrollTrigger } from "gsap/ScrollTrigger";

onMounted(() => {
  gsap.registerPlugin(ScrollTrigger);

  gsap.to(".header", {
    scrollTrigger: {
      trigger: ".con",
      start: "1%",
      toggleActions: "play pause resume reset",
      end: "bottom bottom",
      scrub: true,
      markers: true,
    },
    backgroundColor: "#000",
  });
});
</script>

<template>
  <view-header class="header" />
  <div class="con">
    <NuxtPage />
  </div>
</template>

<style scoped>
.header {
  position: fixed;
  top: 0;
}
</style>
