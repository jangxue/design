<script setup>
import { onMounted } from "vue";
import { gsap } from "gsap";
import { ScrollTrigger } from "gsap/ScrollTrigger";

onMounted(() => {
  const myElBottom = document.querySelector(".bottom");
  gsap.registerPlugin(ScrollTrigger);

  ScrollTrigger.create({
    trigger: myElBottom,
    start: "top top",
    end: "bottom top",
    pin: false,
    pinSpacing: false,
    onUpdate: (self) => {
      const progress = self.progress;
      const offset = -300;
      const moveX = progress * offset;
      gsap.to(myElBottom, { x: moveX });
    },
  });

  let myElTitle = document.querySelector(".about-title");
  let chars = myElTitle.textContent.split("");

  myElTitle.innerHTML = chars.map((c) => `<span>${c}</span>`).join("");

  let spans = Array.from(myElTitle.querySelectorAll("span"));

  spans.forEach((span, i) => {
    gsap.fromTo(
      span,
      { autoAlpha: 0 },
      {
        autoAlpha: 1,
        scrollTrigger: {
          trigger: ".about-layout",
          start: "top bottom",
          end: "bottom bottom",
        //   scrub: true,
          onUpdate: (self) => {
            let progress = self.progress;
            let targetIndex = Math.floor(progress * spans.length);
            if (i <= targetIndex) {
              gsap.to(span, { autoAlpha: 1 });
            } else {
              gsap.to(span, { autoAlpha: 0 });
            }
          },
        },
      }
    );
  });
});
</script>
<template>
  <!-- background -->
  <div class="back" />
  <!-- back -->
  <view-background />
  <!-- main home layout -->
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
  <!-- container layout -->
  <div class="layout">
    <div class="about-layout">
      <main class="about-title-layout">
        <h1>We are fringe figures in fringe science</h1>
        <p class="about-title">
          Jiangxue Design was founded in 2020, offering free design services to
          teams it believes in based on design investment, and upon their
          success, receiving 0~15% of their market value. We search worldwide
          for teams with various innovative ideas and offer full-stack design
          and development, as well as security support.
        </p>
      </main>
    </div>
    <div class="team-layout">
      <main class="team-layout-title">
        <h1>Team</h1>
      </main>
    </div>
  </div>
</template>

<style scoped>
/* container */
.layout {
  z-index: 0;
  height: 300vh;
  position: relative;
  width: 100vw;
}

/* about */
.about-layout {
  top: 100vh !important;
  position: absolute;
  background: rgb(0, 0, 0);
  width: 100%;
  height: 100vh;
}
.team-layout {
  top: 200vh !important;
  position: absolute;
  background: #f2f2f2;
  width: 100%;
  height: 100vh;
}
.team-layout-title {
  display: flex;
  margin: 0 auto;
  flex-direction: row;
  align-items: flex-start;
  margin-top: 19rem;
}
.team-layout-title h1 {
  font-family: "Poppins", sans-serif;
  font-weight: 400;
  font-size: 1.7rem;
  width: 18%;
  color: #000;
  position: sticky !important;
  top: -1px;
  margin-left: 2rem;
  margin-right: 2rem;
  padding-right: 30px;
  border-right: 2px solid #003eff;
}
.about-layout h1 {
  font-family: "Poppins", sans-serif;
  font-weight: 400;
  font-size: 1.7rem;
  width: 18%;
  color: #ffffff;
  position: sticky !important;
  top: -1px;
  margin-left: 2rem;
  margin-right: 2rem;
  padding-right: 30px;
  border-right: 2px solid #003eff;
}

.about-title-layout {
  display: flex;
  margin: 0 auto;
  flex-direction: row;
  align-items: flex-start;
  margin-top: 19rem;
}
.about-layout .about-title {
  font-size: 1.5rem;
  padding: 2rem;
  padding-top: 0;
  line-height: 1.5;
  color: #ffffff;
  position: sticky !important;
  width: 50%;
  font-family: "Poppins", sans-serif;
  font-weight: 300;
  text-align: justify;
}

/* scr */
.scr {
  margin-top: 3rem;
}
.scr-title {
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
  z-index: 10;
  height: 100%;
  position: absolute;
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
  font-family: "Big Shoulders Text", sans-serif;
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

/* back */
.back {
  background-image: url("/img/res/back.png");
  width: 100%;
  height: 100%;
  z-index: 1;
  display: block;
  position: absolute;
}
</style>
