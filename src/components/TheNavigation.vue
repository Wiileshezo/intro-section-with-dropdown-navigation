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
        <li><RouterLink class="link" to="/">Login</RouterLink></li>
        <li>
          <RouterLink class="link register" to="/">Register</RouterLink>
        </li>
      </ul>
      <!-- <ul class="right-nav">
      </ul> -->
      <div
        class="icon icon-menu"
        v-show="mobile"
        @click="toggleMobileNav"
        :class="{ 'icon-active': mobileNav }"
      ></div>
      <Transition name="mobile-nav">
        <ul v-show="mobileNav" class="dropdown-nav">
          <li><RouterLink class="link" to="/">Features</RouterLink></li>
          <li><RouterLink class="link" to="/">Company</RouterLink></li>
          <li><RouterLink class="link" to="/">Careers</RouterLink></li>
          <li><RouterLink class="link" to="/about">About</RouterLink></li>
          <li><RouterLink class="link" to="/">Login</RouterLink></li>
          <li>
            <RouterLink class="link register" to="/">Register</RouterLink>
          </li>
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
      scrollNav: null,
      mobile: null,
      mobileNav: null,
      windowWidth: null,
    };
  },
  created() {
    window.addEventListener("resize", this.checkScreen);
    this.checkScreen();
    console.log("it work");
  },

  mounted() {
    window.addEventListener("scroll", this.updateScroll);
  },

  // unmounted() {
  //   window.removeEventListener("resize", this.checkScreen);
  // },

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
      this.windowWidth = Window.innerWidth;
      if (this.windowWidth <= 780) {
        this.mobile = true;
        console.log("it work");
      }
      this.mobile = false;
      this.mobileNav = false;
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
  position: relative;
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

.link:active,
.link:hover {
  color: var(--Almost-Black);
}

img {
  padding-inline-end: 2rem;
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
  top: 2rem;
  right: 3rem;
}
.icon-menu {
  background-image: url("../images/icon-menu.svg");
  background-repeat: no-repeat;
  width: 3rem;
  height: 2rem;
  transition: 0.8s ease all;
}

/* .icon-active {
} */

.dropdown-nav {
  display: flex;
  flex-direction: column;
  position: fixed;
  width: 100%;
  height: 100%;
  max-width: 30rem;
  background-color: var(--Almost-White);
  top: 0;
  /* right: 0; */
  left: 0;
}

.dropdown-nav > li {
  margin-right: 0;
  color: var(--Almost-Black);
  font-size: 3rem;
  padding: 2rem;
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
  transform: translateX(-250px);
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
  .left-nav {
    justify-content: none;
  }
}

@media screen and (min-width: 768px) {
}

@media screen and (min-width: 1440px) {
}
</style>
