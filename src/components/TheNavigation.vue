<template>
  <header :class="{ 'scrolled-nav': scrollNav }">
    <nav class="nav">
      <div class="logo">
        <img src="../images/logo.svg" alt="logo" />
      </div>
      <ul v-show="!mobile" class="left-nav">
        <li><RouterLink class="link" to="/">Features</RouterLink></li>
        <li><RouterLink class="link" to="/">Company</RouterLink></li>
        <li><RouterLink class="link" to="/">Careers</RouterLink></li>
        <li><RouterLink class="link" to="/about">About</RouterLink></li>
      </ul>
      <ul v-show="!mobile" class="right-nav">
        <li><RouterLink class="link" to="/">Login</RouterLink></li>
        <li>
          <RouterLink class="link register" to="/">Register</RouterLink>
        </li>
      </ul>
      <div
        class="icon icon-menu"
        v-show="mobile"
        @click="toggleMobileNav"
        :class="{ 'icon-active': mobileNav }"
      ></div>
      <Transition name="mobile-nav">
        <ul v-show="mobileNav" class="dropdown-nav">
          <div class="icon icon-close-menu" @click="toggleMobileNav"></div>
          <li class="pt-5">
            <RouterLink class="link" to="/">Features</RouterLink>
          </li>
          <li><RouterLink class="link" to="/">Company</RouterLink></li>
          <li><RouterLink class="link" to="/">Careers</RouterLink></li>
          <li><RouterLink class="link" to="/about">About</RouterLink></li>
          <li class="center pt-5">
            <RouterLink class="link" to="/">Login</RouterLink>
          </li>
          <li class="center">
            <RouterLink class="link register" to="/">Register</RouterLink>
          </li>
        </ul>
      </Transition>
      <div class="backdrop" @click="toggleMobileNav" v-if="mobileNav"></div>
    </nav>
  </header>
</template>
<script>
import { RouterLink } from "vue-router";
export default {
  emits: ["close"],
  data() {
    return {
      scrollNav: null,
      mobile: null,
      mobileNav: null,
    };
  },
  created() {
    window.addEventListener("resize", this.checkScreen);
    this.checkScreen();
  },

  mounted() {
    window.addEventListener("scroll", this.updateScroll);
  },

  unmounted() {
    window.removeEventListener("resize", this.checkScreen);
  },

  methods: {
    toggleMobileNav() {
      this.mobileNav = !this.mobileNav;
    },
    updateScroll() {
      const scrollPosition = window.scrollY;
      if (scrollPosition > 50) {
        this.scrollNav = true;
        return;
      }
      this.scrollNav = false;
    },
    checkScreen() {
      const windowWidth = window.innerWidth;
      if (windowWidth <= 780) {
        this.mobile = true;
        return;
      }
      this.mobile = false;
      this.mobileNav = false;
      return;
    },
  },
};
</script>

<style scoped>
header {
  width: 100%;
  z-index: 99;
  top: -1px;
  position: fixed;
  transition: 0.5s ease all;
  background-color: var(--Almost-White);
}
.nav {
  position: relative;
  display: flex;
  align-items: center;
  flex-direction: row;
  flex-wrap: nowrap;
  justify-content: space-between;
  padding: 1.5rem;
  transition: 0.5s ease all;
}

a {
  text-align: center;
  padding: 1rem;
  text-decoration: none;
  color: var(--Medium-Gray);
}

.link:active,
.link:hover {
  color: var(--Almost-Black);
}

img {
  width: 6rem;
  transition: 0.5s ease all;
}
.left-nav {
  display: flex;
  align-items: center;
  flex: 1;
  justify-content: flex-start;
}
.right-nav {
  float: right;
  display: flex;
  align-items: center;
}

.icon {
  display: flex;
  align-items: center;
  position: absolute;
  top: 1.5rem;
  width: 3rem;
  height: 2rem;
  transition: 0.8s ease all;
  background-repeat: no-repeat;
}
.icon-menu {
  background-image: url("../images/icon-menu.svg");
  right: 1rem;
}
.icon-close-menu {
  background-image: url("../images/icon-close-menu.svg");
  right: 0;
}
/* .icon-active {
} */

.dropdown-nav {
  display: flex;
  flex-direction: column;
  position: fixed;
  width: 100%;
  height: 100%;
  max-width: 14rem;
  background-color: var(--Almost-White);
  top: 0;
  right: 0;
  margin: 0;
  padding: 0;
}

.dropdown-nav > li {
  margin-right: 0;
  color: var(--Almost-Black);
  font-size: 1rem;
  padding: 1rem;
}

.backdrop {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  z-index: -3;
  background-color: rgba(0, 0, 0, 0.75);
}
.pt-5 {
  padding-top: 5rem !important;
}

.center {
  align-self: center;
  padding-top: 8rem;
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

.scrolled-nav {
  box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.2), 0 6px 20px 0 rgba(0, 0, 0, 0.19);
}

.mobile-nav-enter-from,
.mobile-nav-leave-to {
  transform: translateX(250px);
}
.mobile-nav-enter-active {
  transition: 0.5s ease-out all;
}
.mobile-nav-leave-active {
  transition: 0.3s ease-in all;
}

.mobile-nav-enter-to,
.mobile-nav-leave-from {
  transform: translateX(0);
}

@media screen and (max-width: 450px) {
  .register {
    padding: 0.7rem 2rem;
  }
}

@media screen and (min-width: 768px) {
}

@media screen and (min-width: 1440px) {
}
</style>
