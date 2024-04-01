<template>
  <div ref="container">
    <div ref="follower" class="follower"></div>
    <view-header class="header" />
    <div class="con">
      <NuxtPage />
    </div>
  </div>
</template>

<script setup lang="ts">
import { ref, onMounted, onUnmounted } from "vue";
import { gsap } from "gsap";
import { ScrollTrigger } from "gsap/ScrollTrigger";
import Lenis from "@studio-freight/lenis";

interface LenisEvent {
  target: Lenis;
  type: string;
  [key: string]: unknown;
}

const container = ref<HTMLElement | null>(null);
const follower = ref<HTMLElement | null>(null);

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

  const containerElem = container.value as HTMLElement;
  const followerElem = follower.value as HTMLElement;

  const mouseMoveHandler = (event: MouseEvent) => {
    gsap.to(followerElem, {
      duration: 0.3,
      x: event.clientX - containerElem.offsetLeft,
      y: event.clientY - containerElem.offsetTop,
    });
  };

  containerElem.addEventListener("mousemove", mouseMoveHandler);

  const lenis: Lenis = new Lenis();
  if (typeof window !== "undefined") {
    lenis.on("scroll", (e: LenisEvent) => {
      console.log(e);
    });
    function raf(time: number) {
      lenis.raf(time);
      requestAnimationFrame(raf);
    }
    requestAnimationFrame(raf);
  }

  onUnmounted(() => {
    containerElem.removeEventListener("mousemove", mouseMoveHandler);
  });
});
</script>

<style scoped>
.header {
  position: fixed;
  top: 0;
}
.follower {
  position: absolute;
  width: 10rem;
  height: 1rem;
  background-color: #1100ff;
  border-radius: 100%;
}
</style>
