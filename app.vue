<!-- app.vue - for global HTML and Scripts-->

<script setup>
    import main from '~/assets/css/main.css';
    import SiteNavbar from '~/components/SiteNavbar.vue';
    import SiteFooter from '~/components/SiteFooter.vue';
</script>

<template>
    <div class="app-container">
        <SiteNavbar />

        <div class="content">
            <NuxtPage />
        </div>

        <SiteFooter />
    </div>
</template>
  
<style scoped>
    .app-container {
    display: flex;
    flex-direction: column;
    min-height: 100vh;
  }
  
  .content {
    flex-grow: 1;
  }
</style>
  