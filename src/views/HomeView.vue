<script></script>

<template>
  <div class="container">
    <div class="section1">
      <h1>Make remote work</h1>
      <p>
        Get your team in sync, no matter your location. Streamline processes,
        create team rituals, and watch productivity soar.
      </p>
      <button>Learn more</button>
      <div class="imgs-client">
        <img src="../images/client-databiz.svg" alt="" />
        <img src="../images/client-audiophile.svg" alt="" />
        <img src="../images/client-meet.svg" alt="" />
        <img src="../images/client-maker.svg" alt="" />
      </div>
    </div>
    <div class="section2">
      <img
        src="../images/image-hero-desktop.png"
        alt="image-hero"
        class="img-hero"
      />
    </div>
  </div>
</template>

<style scoped>
.container {
  display: flex;
  /* padding-inline: 6rem; */
  align-items: center;
  padding-top: 10rem;
}
h1 {
  font-size: 5.6rem;
  margin: 0;
  color: var(--Almost-Black);
}
p {
  color: var(--Medium-Gray);
  font-size: 1.3rem;
  padding-inline-end: 6rem;
  line-height: 2rem;
  margin-block: 2rem;
}
button {
  padding: 1rem 2rem;
  border-radius: 1rem;
  font-size: 1.3rem;
  color: var(--Almost-White);
  background-color: var(--Almost-Black);
  border: 0;
}
.section1 {
  padding: 0 2rem;
  display: flex;
  flex-direction: column;
  align-items: flex-start;
  width: 55vw;
  box-sizing: border-box;
}
.img-hero {
  width: 45vw;
  height: 70vh;
}
.imgs-client {
  display: flex;
  padding: 5rem 1rem 0;
  align-items: center;
  justify-content: center;
}
.imgs-client > img {
  padding: 1.5rem;
}
</style>
