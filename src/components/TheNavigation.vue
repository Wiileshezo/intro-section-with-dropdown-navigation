<template>
  <header>
    <nav class="nav">
      <div class="left-nav">
        <img src="../images/logo.svg" alt="logo" />
        <RouterLink to="/">Features</RouterLink>
        <RouterLink to="/">Company</RouterLink>
        <RouterLink to="/">Careers</RouterLink>
        <RouterLink to="/about">About</RouterLink>
      </div>
      <div class="right-nav">
        <RouterLink to="/">Login</RouterLink>
        <RouterLink to="/">Register</RouterLink>
      </div>
      <!-- <RouterLink
                href="javascript:void(0);"
                class="icon"
                @click="responsiveNav"
                ></RouterLink> -->
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
.nav {
  overflow: hidden;
  display: flex;
  align-items: center;
  flex-direction: row;
  flex-wrap: nowrap;
  justify-content: space-between;
  padding: 2rem;
}

a {
  text-align: center;
  padding: 1rem;
  text-decoration: none;
  color: var(--Medium-Gray);
}

a.active,
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
}

.topnav .icon {
  display: none;
}

@media screen and (max-width: 375px) {
  .nav a:not(:first-child) {
    display: none;
  }
  .nav a.icon {
    float: right;
    display: block;
  }
}

@media screen and (max-width: 600px) {
  .topnav.responsive {
    position: relative;
  }
  .topnav.responsive .icon {
    position: absolute;
    right: 0;
    top: 0;
  }
  .topnav.responsive a {
    float: none;
    display: block;
    text-align: left;
  }
}
</style>
