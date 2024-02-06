<script setup>
import { RouterLink, RouterView } from "vue-router";
</script>

<template>
  <header>
    <img src="./images/logo.svg" alt="logo" />
    <nav>
      <RouterLink to="/Features">Features</RouterLink>
      <RouterLink to="/company">Company</RouterLink>
      <RouterLink to="/careers">Careers</RouterLink>
      <RouterLink to="/about">About</RouterLink>
      <RouterLink to="/login">Login</RouterLink>
      <RouterLink to="/register">Register</RouterLink>
    </nav>
  </header>

  <RouterView />

  <div>
    <h1>Make remote work</h1>
    <p>
      Get your team in sync, no matter your location. Streamline processes,
      create team rituals, and watch productivity soar.
    </p>
    <button>Learn more</button>
  </div>
</template>

<style scoped></style>
