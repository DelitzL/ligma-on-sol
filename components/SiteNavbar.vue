<template>
  <nav class="navbar">
    <!-- Navbar Brand with Logo and Text -->
    <div class="navbar-brand">
      <a href="/">
        <img src="~/assets/image/mascot/ligma-coin.png" alt="Ligma Logo" class="navbar-logo" />
      </a>
      <h1 class="navbar-title">$LIGMA ON SOL</h1>
    </div>

    <!-- Navbar Toggle for Mobile -->
    <button class="navbar-toggle" @click="isMenuOpen = !isMenuOpen">
      ☰
    </button>

    <!-- Navbar Links -->
    <ul class="navbar-links" :class="{ open: isMenuOpen }">
      <li><a href="/">Home</a></li>
      <li><a href="/about">About</a></li>
      <li><a href="/memecreator">Meme Creator</a></li>
      <li><a href="/tweets">Tweets</a></li>
      <li><a href="/games">Games</a></li>
      <li><a href="/updates">Updates</a></li>
      <li><a href="/buynow">BUY NOW!</a></li>
    </ul>
  </nav>
</template>

<script setup>
import { ref } from 'vue';

const isMenuOpen = ref(false);
</script>

<style scoped>
.navbar {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 20px 20px;
  background-color: var(--color-primary);
  color: var(--color-light);
}

/* Flex container for brand logo and text */
.navbar-brand {
  display: flex;
  align-items: center; /* Aligns logo and text vertically */
  gap: 10px; /* Space between the logo and text */
}

/* Logo styling */
.navbar-logo {
  height: 100px; /* Adjust the logo height */
  width: auto; /* Maintain aspect ratio */
}

/* Text styling for $LIGMA */
.navbar-title {
  font-size: 1.5rem; /* Adjust text size */
  font-weight: bold;
  color: var(--color-light);
  margin: 0; /* Remove default margin */
}

/* Navbar Toggle Button */
.navbar-toggle {
  display: none;
  background: none;
  border: none;
  color: var(--color-light);
  font-size: 1.5rem;
  cursor: pointer;
}

/* Navbar Links */
.navbar-links {
  list-style: none;
  display: flex;
  gap: 30px;
  margin: 0;
  padding: 0;
}

.navbar-links a {
  text-decoration: none;
  color: var(--color-light);
  font-weight: 500;
}

.navbar-links a:hover {
  text-decoration: underline;
}

@media (max-width: 768px) {
  .navbar-toggle {
    display: block;
  }

  .navbar-links {
    display: none;
    flex-direction: column;
    gap: 10px;
    background-color: var(--color-primary);
    position: absolute;
    top: 50px;
    right: 20px;
    padding: 10px 20px;
    border-radius: 5px;
  }

  .navbar-links.open {
    display: flex;
  }
}
</style>
