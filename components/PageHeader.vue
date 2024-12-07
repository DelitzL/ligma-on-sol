<script setup>
defineProps({
  title: {
    type: String,
    required: true,
  },
  subtitle: {
      type: String,
      required: false,
  },
});
</script>

<template>
    <div class="page-header">
      <h1>{{ title }}</h1>
      <p>{{ subtitle }}</p>
    </div>
</template>
  

<style scoped>
.page-header {
  text-align: left;
  padding: 50px 50px 50px 50px;
  background-color: var(--color-primary);
  box-shadow: 0px 4px 6px rgba(0, 0, 0, 0.5);
}
</style>



  