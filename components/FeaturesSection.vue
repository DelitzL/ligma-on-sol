<template>
    <div class="features-section">
      <h2>Features</h2>
      <div class="features">
        <div v-for="(feature, index) in features" :key="index" class="feature-card">
          <h3>{{ feature.title }}</h3>
          <p>{{ feature.description }}</p>
        </div>
      </div>
    </div>
  </template>
  
  <script setup>
  const features = [
    { title: 'Feature One', description: 'Description of feature one.' },
    { title: 'Feature Two', description: 'Description of feature two.' },
    { title: 'Feature Three', description: 'Description of feature three.' },
  ];
  </script>
  
  <style scoped>
  .features-section {
    padding: 40px;
  }
  .features {
    display: flex;
    gap: 20px;
  }
  .feature-card {
    flex: 1;
    padding: 20px;
    border: 1px solid #ddd;
    border-radius: 10px;
    background-color: #ddd;
  }
  </style>
  