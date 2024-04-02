<script setup>
import { BrandTwitter, BrandGithub, BrandBehance } from "@vicons/tabler";
</script>

<template>
  <main>
    <BrandTwitter />
    <BrandGithub />
    <BrandBehance />
  </main>
</template>

<style scoped>
main {
  display: flex;
  flex-direction: column;
  background-color: #000;
  list-style-type: none;
  grid-gap: 1rem;
  gap: 1rem;
  position: fixed;
  inset-inline-end: 0;
  z-index: 99;
  top: 50%;
  -webkit-transform: translateY(-50%);
  transform: translateY(-50%);
  padding: 25px;
  align-items: center;
  transition: color 4s;
}
main svg {
  width: 25px;
  color: rgb(134 134 134 / 61%);
  cursor: pointer;
}
</style>
