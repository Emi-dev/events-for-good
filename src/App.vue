<script setup>
import { RouterLink, RouterView } from "vue-router";
</script>

<template>
  <div id="layout">
    <header>
      <div class="wrapper">
        <nav>
          <!-- use ":to" instead of "to" here since dynamically binding the path. -->
          <RouterLink :to="{ name: 'event-list' }">Events</RouterLink> |
          <RouterLink :to="{ name: 'about' }">About</RouterLink>
        </nav>
      </div>
    </header>
    <RouterView />
  </div>
</template>

<!-- Non scoped style can be applied in App.vue as global styles -->
<style>
#layout {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

nav {
  padding: 30px;
}

nav a {
  font-weight: bold;
  color: #2c3e50;
}

nav a.router-link-exact-active {
  color: #42b983;
}

h2 {
  font-size: 1.5rem;
}
</style>
