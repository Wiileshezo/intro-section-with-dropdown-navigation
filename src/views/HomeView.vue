<script></script>

<template>
  <div class="container">
    <div class="section1">
      <img
        src="../images/image-hero-mobile.png"
        alt="image-hero"
        class="hero-img"
      />
    </div>
    <div class="section2">
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
  </div>
</template>

<style scoped>
.container {
  display: flex;
  flex-direction: column;
  align-items: center;
  box-sizing: border-box;
  padding-top: 5rem;
}
h1 {
  margin: 0;
  color: var(--Almost-Black);
  font-size: 2.3rem;
}
p {
  color: var(--Medium-Gray);
  font-size: 1rem;
  line-height: 1.5rem;
  margin-block: 2rem;
}
button {
  border-radius: 0.7rem;
  color: var(--Almost-White);
  background-color: var(--Almost-Black);
  border: 2px solid var(--Almost-Black);
  padding: 0.7rem 2rem;
  font-size: 1rem;
  font-weight: 700;
}

button:hover,
button:active {
  background-color: var(--Almost-White);
  color: var(--Almost-Black);
}

.section1 {
  display: flex;
  /* background-image: url("../images/image-hero-mobile.png"); */
  background-repeat: no-repeat;
}
.section2 {
  display: flex;
  flex-direction: column;
  align-items: center;
  padding-inline: 2rem;
  text-align: center;
}
.hero-img {
  width: 100vw;
  height: 60vh;
  padding-block: 1rem 3rem;
}
.imgs-client {
  display: flex;
  align-items: center;
  justify-content: center;
  margin-block-start: 3rem;
}
.imgs-client > img {
  padding: 0.5rem;
  width: 4rem;
}
</style>
