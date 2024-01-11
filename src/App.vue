<script setup>
import { RouterLink, RouterView } from 'vue-router'
</script>

<template>
  <header>

    <div class="wrapper">

      <nav class="navbar">
        <RouterLink  class="navbar-item" to="/">Home</RouterLink>
        <RouterLink class="navbar-item" to="/about">About</RouterLink>
        <RouterLink class="navbar-item" to="/contact">contact</RouterLink>
        <RouterLink class="navbar-item" to="/shop">Shop</RouterLink>
      </nav>
    </div>
  </header>

  <RouterView />
</template>

<style >
</style>
