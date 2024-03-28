<script setup>
import { ref } from "vue";

const scrollTexts = ref([
  "TRLAB",
  "THESIS",
  "LI.FINANCE",
  "TRLAB",
  "THESIS",
  "LI.FINANCE",
  "TRLAB",
  "THESIS",
  "LI.FINANCE",
  "TRLAB",
  "THESIS",
  "LI.FINANCE",
]);
</script>
<template>
  <view-background />
  <main class="bottom">
    <div class="bottom-layout">
      <div class="title">
        <div class="title-layout">
          <p>JIANGXUE</p>
        </div>
        <an-font
          class="span"
          :text="[
            'CALCULATE PROJECTS',
            'SECURITY RESEARCH',
            'DISTRIBUTED COMPUTING',
          ]"
        />
      </div>
      <p class="f">design team</p>
      <div class="scr">
        <p class="scr-title">INVESTMENTS</p>
        <an-scroll class="scr-scroll" />
      </div>
    </div>
  </main>
</template>

<style scoped>
/* scr */
.scr {
  margin-top: 3rem;
}
.scr-title {
  font-family: "3270NerdFontRegular";
  background: #ffffff;
  color: #000;
  padding: 0.3rem;
  font-size: 17px;
  margin-left: 0px;
  width: fit-content;
}
.scr-scroll {
  margin-top: 1rem;
  height: 10rem;
}
/* layout */
.bottom {
  z-index: 1000;
  position: absolute;
  /* aspect-ratio: 16/9; */
  height: 100%;
  width: -webkit-fill-available;
}
.bottom-layout {
  padding-left: 2rem;
  padding-right: 2rem;
}
.title {
  display: flex;
  text-transform: uppercase;
  aspect-ratio: 16/6;
  align-items: flex-end;
}
.f {
  text-transform: uppercase;
}
.title-layout {
  display: flex;
  flex-direction: column;
}

.span {
  margin: 0;
  color: #0743ff;
  line-height: 1;
  font-family: "Big Shoulders Text";
  font-size: 4.6em;
}
p {
  margin: 0;
  line-height: 1;
  color: #ffffff;
  font-family: "Poppins";
  font-size: 5em;
  margin-right: 1rem;
}
</style>
