<template>
  <main>
    <div class="layout">
      <div class="logo">
        <img src="/img/logo/sif-logo-w.svg" alt="logo" />
        <p>The combination of design and investment.</p>
      </div>
      <div>
        <img src="/img/res/menu.svg" alt="menu" />
      </div>
    </div>
  </main>
</template>

<style scoped>
main {
  position: absolute;
  z-index: 999;
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
  background: #ffffff;
  color: #000;
  padding: 0.3rem;
  margin-left: 3rem;
}
</style>
