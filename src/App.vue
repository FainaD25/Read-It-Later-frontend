<script setup>
import { RouterLink, RouterView } from 'vue-router'
import HelloWorld from './components/HelloWorld.vue'
import {ref} from 'vue';

const authenticated = ref(() => {
  const token = localStorage.getItem('user-token');
  return !(!token); // boolean if token exists
});

</script>

<template>
  <header>
    <div class="header-content">
      <img alt="ReadItLater logo" class="logo" src="@/assets/owl.svg" width="125px" height="125" />
      <HelloWorld msg="Read It Later" />
    </div>

    <nav>
      <RouterLink to="/">Home</RouterLink>
      <RouterLink v-if="authenticated()" to="/recommended">Recommended</RouterLink>
      <RouterLink v-if="authenticated()" to="/wishlist">Wishlist</RouterLink>
      <RouterLink to="/about">About</RouterLink>
      <RouterLink to="/profile">Profile</RouterLink>
    </nav>
  </header>

  <RouterView />
</template>

<style scoped>
header {
  position: sticky;
  top: 0;
  left: 0;
  width: 100%;
  z-index: 100;
  background-color: var(--color-pink-lavender-darker);
  box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);
  margin-bottom: 2vw;
}

.header-content {
  display: flex;
  flex-direction: column;
  align-items: center; /* Vertically center-aligns logo and text */
  margin-left: 2vw;
}

.logo {
  display: block;
}

nav {
  width: 100%;
  font-size: 14px;
  text-align: center;
  margin-top: 1rem;
  margin-bottom: 1vw;
}

nav a {
  display: inline-block;
  padding: 0 1rem;
  border-left: 1px solid var(--color-space-cadet);
}

nav a:first-of-type {
  border: 0;
}

@media (min-width: 1024px) {

  .header-content {
    flex-direction: row;
    align-items: center; /* Vertically center-aligns logo and text */
  }

  .logo {
    margin: 0 2rem 0 0;
  }


  nav {
    text-align: left;
    margin-left: 1rem;
    font-size: 1rem;

    margin-top: 1rem;
  }
}
</style>
