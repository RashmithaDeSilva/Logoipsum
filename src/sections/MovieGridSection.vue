<script setup>
import { ref } from 'vue';
import search from '../assets/Icons/Search White.svg';
import batman from '../assets/Images/Batman.jpg';
import wildWest from '../assets/Images/Wild West.jpg';
import spiderman from '../assets/Images/Spiderman.jpg';
import close from '../assets/Icons/Close White.svg';

const items = ref([
  {
    image: batman,
    title: 'Batman Returns',
    description: 'Lorem ipsum dolor sit amet, consetetur sadipscing elitr, sed diam nonumy eirmod tempor invidunt ut…'
  },
  {
    image: wildWest,
    title: 'Wild Wild West',
    description: 'Lorem ipsum dolor sit amet, consetetur sadipscing elitr, sed diam nonumy eirmod tempor invidunt ut…'
  },
  {
    image: spiderman,
    title: 'The Amazing Spiderman',
    description: 'Lorem ipsum dolor sit amet, consetetur sadipscing elitr, sed diam nonumy eirmod tempor invidunt ut…'
  },
]);

const removeItem = (index) => {
  items.value.splice(index, 1);
};
</script>

<template>
  <section class="movie-section">
    <div class="header-bar">
      <h1>Collect your favourites</h1>
      <div class="search-box">
        <img :src="search" alt="Search Icon" class="search-icon" />
        <input type="text" placeholder="Search title and add to grid" />
      </div>
    </div>

    <hr />

    <div class="grid-container">
      <div v-for="(item, index) in items" :key="index" class="item-card">
        <div class="image-container">
          <img class="movie-image" :src="item.image" :alt="item.title" />
          <div class="close-div">
            <button class="close-button" @click="removeItem(index)">
              <img :src="close" alt="Close Icon" />
            </button>
          </div>
        </div>
        <div class="item-content">
          <h4>{{ item.title }}</h4>
          <p>{{ item.description }}</p>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
.movie-section {
  padding: 2rem;
  background-color: rgb(36, 34, 34);
  color: white;
}

/* Header and search bar container */
.header-bar {
  display: flex;
  justify-content: space-between;
  align-items: center;
  flex-wrap: wrap;
  gap: 1rem;
  margin-bottom: 1.5rem;
}

/* Mobile: Stack header under input */
@media (max-width: 639px) {
  .header-bar {
    flex-direction: column-reverse;
    align-items: flex-start;
  }
}

h1 {
  font-size: 1.5rem;
  margin: 0;
}

.search-box {
  position: relative;
  width: 100%;
  max-width: 400px;
}

.search-box input {
  width: 100%;
  padding: 0.75rem 1rem 0.75rem 2.5rem;
  border: none;
  border-radius: 4px;
  font-size: 1rem;
  background-color: rgb(36, 34, 34);
  border: 1px solid white;
}

.search-icon {
  position: absolute;
  left: 0.75rem;
  top: 50%;
  transform: translateY(-50%);
  width: 20px;
  height: 20px;
}

hr {
  margin: 1.5rem 0;
  border: 0;
  height: 1px;
  background-color: #333;
}

.grid-container {
  display: grid;
  grid-template-columns: 1fr;
  gap: 1.5rem;
}

/* Tablet */
@media (min-width: 640px) {
  .grid-container {
    grid-template-columns: repeat(2, 1fr);
  }
}

/* Desktop */
@media (min-width: 1024px) {
  .grid-container {
    grid-template-columns: repeat(3, 1fr);
  }
}

.item-card {
  background-color: #414040;
  border-radius: 8px;
  overflow: hidden;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.3);
  display: flex;
  flex-direction: column;
}

.image-container {
  position: relative;
  width: 100%;
  height: 600px; 
  overflow: hidden;
}

.movie-image {
  width: 100%;
  height: 100%;
  object-fit: cover;
  display: block;
}

.close-button {
  position: absolute;
  top: 0.5rem;
  right: 0.5rem;
  background-color: rgb(36, 34, 34); 
  padding: 1rem; 
  display: flex;
  align-items: center;
  justify-content: center;
  border: none;
  cursor: pointer;
}


.close-button img {
  width: 100%;
  height: 100%;
}


.item-content {
  padding: 1rem;
}

.item-content h4 {
  margin: 0 0 0.5rem;
  font-size: 1.1rem;
}

.item-content p {
  font-size: 0.95rem;
  color: #ccc;
}
</style>
