<script></script>

<template>
  <div class="container">
    <div class="section1"></div>
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
  padding-top: 6rem;
  margin: auto;
  gap: 3rem;
}
h1 {
  margin: 0;
  color: var(--Almost-Black);
  font-size: 2.2rem;
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
  margin-block-end: 3rem;
}

button:hover,
button:active {
  background-color: var(--Almost-White);
  color: var(--Almost-Black);
}

.section1 {
  display: flex;
  width: 99vw;
  height: 45vh;
  padding-block: 2rem 6rem;
  background-image: url("@/images/image-hero-desktop.png");
  background-repeat: no-repeat;
  background-size: contain;
  background-position: center bottom;
  justify-content: center;
  align-items: center;
  text-align: center;
  margin: auto;
}
.section2 {
  display: flex;
  width: unset;
  flex-direction: column;
  align-items: center;
  text-align: center;
}
.imgs-client {
  display: flex;
  align-items: center;
  justify-content: center;
  margin: auto;
}
.imgs-client > img {
  padding: 0.5rem;
  width: 4rem;
}
@media screen and (max-width: 500px) {
  .section1 {
    background-image: url("@/images/image-hero-mobile.png");
    background-position: center top;
    height: 20vh;
    width: 100vw;
  }
  .section2 {
    padding-inline: 1rem;
    width: 90vw;
  }
}

@media screen and (min-width: 600px) {
  .container {
    flex-direction: row-reverse;
    align-items: flex-end;
    padding-inline: 5rem;
  }
  .section1 {
    width: 50vw;
    height: 30vh;
  }
  .section2 {
    width: 40vw;
    align-items: flex-start;
    text-align: left;
  }
  h1 {
    font-size: 2.7rem;
  }
  p {
    font-size: 0.8rem;
    margin-block: 1rem;
    padding-right: 1rem;
  }
  button {
    margin-block-end: 2rem;
    padding: 0.5rem 1.5rem;
    font-size: 0.8rem;
  }
  .imgs-client > img {
    width: 3.5rem;
  }
}

@media screen and (min-width: 1024px) {
  .container {
    padding-top: 7rem;
  }
  .section1 {
    width: 45vw;
    height: 45vh;
  }
  .section2 {
    width: 50vw;
  }

  h1 {
    font-size: 3.5rem;
    padding-inline: 0 5rem;
  }
  p {
    font-size: 1rem;
    padding-inline: 0 4rem;
  }
  button {
    margin-block-end: 2rem;
    padding: 0.7rem 1.7rem;
    font-size: 1rem;
  }
  .imgs-client > img {
    width: 6rem;
  }
}

@media screen and (min-width: 1400px) {
  .section1 {
    width: 42vw;
    height: 65vh;
  }
  .section2 {
    width: 65vw;
  }
  h1 {
    font-size: 5.5rem;
    padding-inline: 2rem 8rem;
  }

  p {
    font-size: 1.3rem;
    line-height: 2rem;
    padding-inline: 2rem 10rem;
  }
  button {
    padding: 1rem 2rem;
    font-size: 1.5rem;
    margin: 1rem 2rem 6rem;
    border-radius: 1rem;
    border: 5px solid var(--Almost-Black);
  }
  .imgs-client > img {
    width: 8rem;
  }
}
</style>
