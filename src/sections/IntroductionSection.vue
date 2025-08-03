<script setup>
</script>

<template>
  <section class="intro-section">
    <h1>MOVE LIBRARY</h1>
    <h4>
      Lorem ipsum dolor sit amet, consetetur sadipscing elitr, sed diam nonumy eirmod tempor invidunt ut labore et dolore magna aliquyam erat, sed diam voluptua.
    </h4>
  </section>
</template>

<style scoped>
.intro-section {
  padding: 5rem 2rem;
  display: flex;
  flex-direction: column;
  gap: 1rem;
  background-color: black;
}

h1 {
  color: white;
  font-size: 2.5rem;
}

h4 {
  width: 100%; /* Default: mobile */
  color: grey;
  font-size: 1.25rem;
}

/* Tablet: ≥768px */
@media (min-width: 768px) {
  h4 {
    width: 70%;
  }
}

/* Desktop and up: ≥1024px */
@media (min-width: 1024px) {
  h4 {
    width: 40%;
  }
}

@media (min-width: 1536px) {
  .intro-section {
    padding: 5rem 10rem;
  }
}
</style>
