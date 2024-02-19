<template>
  <div>
    <h1>This is an about page</h1>
  </div>
  <div class="grid-container">
    <h1 class="item1">Make remote work</h1>
    <p class="item2">
      Get your team in sync, no matter your location. Streamline processes,
      create team rituals, and watch productivity soar.
    </p>
    <button class="item3">Learn more</button>
    <img src="../images/image-hero-desktop.png" alt="" class="item4" />
    <div class="item5">
      <img src="../images/client-databiz.svg" alt="" />
      <img src="../images/client-audiophile.svg" alt="" />
      <img src="../images/client-meet.svg" alt="" />
      <img src="../images/client-maker.svg" alt="" />
    </div>
  </div>
</template>

<style scoped>
.grid-container {
  display: grid;
  grid-template-columns: 20vw 25vw 5vw 40vw;
  gap: 10px;
  padding-inline: 3rem;
  align-items: end;
}
.item1 {
  grid-area: 2/1/3/3;
  margin: 0;
}
.item2 {
  grid-area: 3/1/4/3;
  margin: 0;
}
.item3 {
  grid-area: 4/1/5/2;
  border-radius: 0.7rem;
  color: var(--Almost-White);
  background-color: var(--Almost-Black);
  border: 2px solid var(--Almost-Black);
  font-size: 1rem;
  padding: 0.7rem 2rem;
  font-weight: 700;
}
.item4 {
  grid-area: 2/4/6/5;
  width: 30vw;
}
.item5 {
  grid-area: 5/1/6/3;
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 1rem;
}
</style>
