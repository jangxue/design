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
    <div class="title">
      <div class="title-layout">
        <an-font
          class="span"
          :text="[
            'CALCULATE PROJECTS',
            'SECURITY RESEARCH',
            'DISTRIBUTED COMPUTING',
          ]"
        />
        <p>JIANGXUE<br />design team</p>
      </div>
    </div>
    <p class="scr-title">INVESTMENTS</p>
    <an-scroll />
  </main>
</template>

<style scoped>
/* scr */
.scr-title {
  font-family: "3270NerdFontRegular";
  background: #ffffff;
  color: #000;
  padding: 0.3rem;
  font-size: 17px;
  margin-left: 0px;
  width: fit-content;
}
/* layout */
.bottom {
  z-index: 1000;
  position: absolute;
  /* aspect-ratio: 16/9; */
  height: 100%;
  width: -webkit-fill-available;
}
.title {
  display: flex;
  text-transform: uppercase;
  aspect-ratio: 16/6;
  align-items: flex-end;
}
.title-layout {
  display: flex;
}

.span {
  margin: 0;
  color: #0743ff;
  line-height: 1;
  font-family: "Big Shoulders Text";
  font-size: 5em;
}
p {
  margin: 0;
  line-height: 1;
  color: #ffffff;
  font-family: "Poppins";
  font-size: 5em;
  margin-left: 1rem;
}
</style>
