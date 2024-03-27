<template>
  <div
    class="animated-text-container"
    @mouseover="startCharByCharAnimation"
    @mouseleave="stopAndResetAnimation"
  >
    <span ref="textElement" class="animated-text">
      <span
        v-for="(char, index) in displayedText"
        :key="index"
        :class="{ transitioning: isAnimating && currentCharIndex > index }"
        >{{ char }}</span
      >
    </span>
  </div>
</template>

<script setup>
import { ref, onMounted, defineProps } from "vue";

const props = defineProps({
  text: {
    type: String,
    required: true,
  },
  ant: {
    type: Boolean,
    default: false,
  }
});

const isAnimating = ref(false);

const { text } = props;

const randomChars = "!@#$%^&*()_+-=[]{}|;:,.<>?";
let timeoutId;
let currentCharIndex = -1;
let displayedText = ref(Array.from(text));

function getRandomChar() {
  return randomChars[Math.floor(Math.random() * randomChars.length)];
}

function animateToRandom() {
  isAnimating.value = true;
  if (currentCharIndex >= text.length) {
    currentCharIndex = text.length - 1;
  }

  if (currentCharIndex >= 0) {
    displayedText.value[currentCharIndex] = getRandomChar();

    timeoutId = setTimeout(() => {
      currentCharIndex--;
      animateToRandom();
    }, 50);
  } else {
    displayedText.value = Array.from(text);
    currentCharIndex = -1;
    isAnimating.value = false;
    clearTimeout(timeoutId);
  }
}

function startCharByCharAnimation() {
  currentCharIndex = text.length - 1;
  animateToRandom();
}

function stopAndResetAnimation() {
  clearTimeout(timeoutId);
  currentCharIndex = -1;
  displayedText.value = Array.from(text);
}

onMounted(() => {
  displayedText.value = Array.from(text);
});
</script>

<style scoped>
.transitioning {
  transition: opacity 0.2s ease-out; 
}
div {
    cursor: pointer;
}
</style>
