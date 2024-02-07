<template>
  <header :class="{ 'scrolled-nav': scrollPosition }">
    <nav class="nav">
      <div class="logo">
        <img src="../images/logo.svg" alt="logo" />
      </div>
      <ul v-show="!mobile" class="left-nav">
        <li><RouterLink class="link" to="/">Features</RouterLink></li>
        <li><RouterLink class="link" to="/">Company</RouterLink></li>
        <li><RouterLink class="link" to="/">Careers</RouterLink></li>
        <li><RouterLink class="link" to="/about">About</RouterLink></li>
        <li><RouterLink class="link" to="/">Login</RouterLink></li>
        <li>
          <RouterLink class="link register" to="/">Register</RouterLink>
        </li>
      </ul>
      <!-- <ul class="right-nav">
      </ul> -->
      <div class="icon icon-menu">
        <span
          v-show="mobile"
          @click="toggleMobileNav"
          :class="{ 'icon-active': mobileNav }"
        ></span>
      </div>
      <Transition name="mobile-nav">
        <ul v-show="mobileNav" class="dropdown-nav">
          <li><RouterLink class="link" to="/">Features</RouterLink></li>
          <li><RouterLink class="link" to="/">Company</RouterLink></li>
          <li><RouterLink class="link" to="/">Careers</RouterLink></li>
          <li><RouterLink class="link" to="/about">About</RouterLink></li>
        </ul>
      </Transition>
    </nav>
  </header>
</template>
<script>
import { RouterLink } from "vue-router";
export default {
  data() {
    return {
      nav: false,
    };
  },
  methods: {
    responsiveNav() {
      console.log("Navigathion");
    },
  },
};
</script>

<style scoped>
header {
  width: 100%;
  z-index: 99;
  position: fixed;
  transition: 0.5s ease all;
  background-color: var(--Almost-White);
}
.nav {
  display: flex;
  align-items: center;
  flex-direction: row;
  flex-wrap: nowrap;
  justify-content: space-between;
  padding: 2rem;
  transition: 0.5s ease all;
}

a {
  text-align: center;
  padding: 1rem;
  text-decoration: none;
  color: var(--Medium-Gray);
}

a:active,
a:hover {
  color: var(--Almost-Black);
}

img {
  padding-inline-end: 2rem;
}
.left-nav {
  display: flex;
  align-items: center;
}
.right-nav {
  float: right;
  display: flex;
  align-items: center;
}

.icon {
  height: 3vh;
}
.icon-menu {
  background-image: url("../images/icon-menu.svg");
  background-repeat: no-repeat;
  width: 3rem;
  height: 2rem;
}

.register {
  border: 2px solid var(--Medium-Gray);
  border-radius: 1rem;
}

.register:active,
.register:hover {
  color: var(--Almost-Black);
  border: 2px solid var(--Almost-Black);
}

ul,
.link {
  font-weight: 500;
  list-style: none;
  text-decoration: none;
}

.link {
  transition: 0.5 ease all;
}

@media screen and (max-width: 375px) {
}

@media screen and (min-width: 1440px) {
}
</style>
