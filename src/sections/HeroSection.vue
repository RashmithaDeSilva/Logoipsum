<script setup>
import HeaderVideo from '../assets/Videos/Header Video.mp4';
</script>

<template>
  <section class="hero-section">
    <video autoplay muted loop playsinline class="hero-video">
      <source :src="HeaderVideo" type="video/mp4" />
      Your browser does not support the video tag.
    </video>
  </section>
</template>

<style scoped>
.hero-section {
  height: calc(100vh - 5.2rem);
  overflow: hidden;
}

.hero-video {
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  object-fit: cover;
  z-index: -1;
  transform: scale(1.2);
}
</style>
