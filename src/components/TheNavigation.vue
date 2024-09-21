<template>
  <header :class="{ 'scrolled-nav': scrollNav }">
    <nav class="nav">
      <div class="logo">
        <img src="../images/logo.svg" alt="logo" />
      </div>
      <ul v-show="!mobile" class="left-nav">
        <li class="dropdown-list">
          <a class="link" href="javascript:void(0)">
            Features
            <img
              src="../images/icon-arrow-down.svg"
              alt="icon-arrow-down"
              class="icon-arrow arrow-up"
            />
          </a>
          <div class="dropdown-list-content right-0">
            <RouterLink to="/">
              <img
                src="../images/icon-todo.svg"
                alt=""
                class="dropdown-list-icon"
              />
              Todo List
            </RouterLink>
            <RouterLink to="/">
              <img
                src="../images/icon-calendar.svg"
                alt=""
                class="dropdown-list-icon"
              />
              Calendar
            </RouterLink>
            <RouterLink to="/">
              <img
                src="../images/icon-reminders.svg"
                alt=""
                class="dropdown-list-icon"
              />
              Reminders
            </RouterLink>
            <RouterLink to="/">
              <img
                src="../images/icon-planning.svg"
                alt=""
                class="dropdown-list-icon"
              />
              planning
            </RouterLink>
          </div>
        </li>
        <li class="dropdown-list">
          <a class="link" href="javascript:void(0)">
            Company
            <img
              src="../images/icon-arrow-down.svg"
              alt="icon-arrow-down"
              class="icon-arrow arrow-up"
            />
          </a>
          <div class="dropdown-list-content">
            <RouterLink to="/">History</RouterLink>
            <RouterLink to="/">Our Team</RouterLink>
            <RouterLink to="/">Blog</RouterLink>
          </div>
        </li>
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
          <div
            class="icon icon-close-menu"
            :aria-expanded="mobileNav"
            @click="toggleMobileNav"
          ></div>
          <li class="pt-5 dropdown-list-mobile" @click="toggleDropdownList">
            <a class="link" href="javascript:void(0)">
              Features
              <img
                src="../images/icon-arrow-down.svg"
                alt="icon-arrow"
                class="icon-arrow"
              />
            </a>
            <div class="dropdown-list-content-mobile">
              <RouterLink to="/">
                <img
                  src="../images/icon-todo.svg"
                  alt=""
                  class="dropdown-list-icon"
                />
                Todo List
              </RouterLink>
              <RouterLink to="/">
                <img
                  src="../images/icon-calendar.svg"
                  alt=""
                  class="dropdown-list-icon"
                />
                Calendar
              </RouterLink>
              <RouterLink to="/">
                <img
                  src="../images/icon-reminders.svg"
                  alt=""
                  class="dropdown-list-icon"
                />
                Reminders
              </RouterLink>
              <RouterLink to="/">
                <img
                  src="../images/icon-planning.svg"
                  alt=""
                  class="dropdown-list-icon"
                />
                planning
              </RouterLink>
            </div>
          </li>
          <li class="dropdown-list-mobile" @click="toggleDropdownList">
            <a class="link" href="javascript:void(0)">
              Company
              <img
                src="../images/icon-arrow-down.svg"
                alt="icon-arrow"
                class="icon-arrow"
              />
            </a>
            <div class="dropdown-list-content-mobile">
              <RouterLink to="/">History</RouterLink>
              <RouterLink to="/">Our Team</RouterLink>
              <RouterLink to="/">Blog</RouterLink>
            </div>
          </li>
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
  data() {
    return {
      scrollNav: null,
      mobile: null,
      mobileNav: null,
      dropdownList: null,
      iconArrow: null,
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
    preventNavigation(e) {
      e.preventDefault();
    },

    toggleDropdownList(e) {
      this.dropdownList = e.target.nextSibling;
      this.iconArrow = e.target.lastChild;
      if (this.dropdownList && this.dropdownList.style) {
        if (
          !this.dropdownList.style.display ||
          this.dropdownList.style.display === "none"
        ) {
          this.dropdownList.style.display = "flex";
          this.iconArrow.src = "icon-arrow-up.svg";
        } else {
          this.dropdownList.style.display = "none";
          this.iconArrow.src = "icon-arrow-down.svg";
        }
      } else {
        console.error("Dropdown list not properly initialized");
      }
    },

    toggleMobileNav() {
      this.mobileNav = !this.mobileNav;
      if (this.mobileNav) {
        document.body.style.overflowY = "hidden";
      } else {
        document.body.style.overflowY = "unset";
      }
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
      return;
    },
  },
  beforeRouteEnter(to, from, next) {
    console.log("The navigation cmp beforeRouteEnter");
    console.log(to, from);
    if (this.mobileNav) {
      next();
    }
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

.dropdown-list {
  position: relative;
}

.dropdown-list:active > a,
.dropdown-list:hover > a {
  color: var(--Almost-Black);
}

.dropdown-list-content {
  display: none;
  position: absolute;
  background-color: #f9f9f9;
  min-width: 10rem;
  box-shadow: 0px 6px 20px 0px rgba(0, 0, 0, 0.2);
  border-radius: 1rem;
  z-index: 1;
  top: 2rem;
  padding: 1rem;
}

.right-0 {
  right: 0;
}

.dropdown-list-content a {
  display: block;
  text-align: left;
  padding: 0.7rem;
}

.dropdown-list-content > a:active,
.dropdown-list-content > a:hover {
  color: var(--Almost-Black);
}
.dropdown-list:hover .dropdown-list-content {
  display: block;
}

.icon-arrow {
  width: 1rem;
}

.dropdown-list-icon {
  width: 1.2rem;
  padding-inline-end: 0.5rem;
  vertical-align: bottom;
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
  overflow-y: scroll;
}

.dropdown-nav > li {
  margin-right: 0;
  color: var(--Almost-Black);
  font-size: 1rem;
  padding: 1rem;
}

.dropdown-list-mobile {
  background-color: var(--Almost-White);
}

.dropdown-list-content-mobile {
  display: none;
  flex-direction: column;
  align-items: flex-start;
  padding: 1rem;
}

.dropdown-list-content-mobile > a {
  padding: 0.5rem;
  margin-left: 1rem;
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

.dropdown-list:active > a .arrow-up,
.dropdown-list:hover > a .arrow-up {
  content: url("../images/icon-arrow-up.svg");
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
    padding: 0.7rem 3.5rem;
  }
}

@media screen and (min-width: 768px) {
}

@media screen and (min-width: 1440px) {
}
</style>
