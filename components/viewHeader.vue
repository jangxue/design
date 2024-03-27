<template>
  <main>
    <div class="layout">
      <div class="logo">
        <img src="/img/logo/sif-logo-w.svg" />
        <p>The combination of design and investment.</p>
      </div>
      <div>
        <img src="/img/res/menu.svg" />
      </div>
    </div>
  </main>
</template>

<style scoped>
main {
  position: absolute;
  z-index: 3;
  width: 100%;
}
.layout {
  display: flex;
  align-items: center;
  justify-content: space-between;
  margin: 0 auto;
  padding: 2rem;
}
.logo {
  display: flex;
}
p {
  font-family: "3270NerdFontRegular";
  background: #ffffff;
  color: #000;
  padding: 0.3rem;
  margin-left: 3rem;
}
</style>
