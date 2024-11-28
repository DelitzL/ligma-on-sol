<template>
    <nav class="navbar">
      <div class="navbar-brand">LOGOTEMP</div>
      <button class="navbar-toggle" @click="isMenuOpen = !isMenuOpen">
        ☰
      </button>
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
    background-color: var(--color-secondary);
    color: var(--color-light);
  }
  
  .navbar-brand {
    font-size: 1.5rem;
    font-weight: bold;
  }
  
  .navbar-toggle {
    display: none;
    background: none;
    border: none;
    color: var(--color-light);
    font-size: 1.5rem;
    cursor: pointer;
  }
  
  .navbar-links {
    list-style: none;
    display: flex;
    gap: 15px;
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
  
  /* Responsive Styles */
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
  