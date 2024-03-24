<script setup>
import ImageUploader from '@/components/organisms/ImageUploader.vue'
</script>

<template>
  <header>
    <div class="logo-container">
      <h1>Header</h1>
    </div>
  </header>

  <main class="body-main">
    <image-uploader />
  </main>
</template>

<style lang="scss" scoped>
@import './assets/_variables';
@import './assets/_breakpoints';

.body-main {
  max-width: $max-width-app;
  display: flex;
  justify-content: center;
  margin: 0 auto;
}

@media (min-width: $breakpoint-ipad) {
  header {
    display: flex;
    justify-content: center;
  }

  .logo {
    margin: 0 2rem 0 0;
  }
}
</style>
