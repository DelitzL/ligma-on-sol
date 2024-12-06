<script setup>
  import ligmaImage from '~/assets/image/mascot/ligma-no-bg.png';
</script>

<template>
  <PageHeaderIndex 
    :imageSrc="ligmaImage" 
    title="$LIGMA ON SOL" 
    subtitle="The coin that is more than just a meme." 
    btntext="BUY" 
  />

      <FeaturesSection />

      <h1 class="text-3xl font-bold underline">
        This is a tailwindcss test, this text should be larger, bold, and underlined.
      </h1>
      
  </template>