<script setup>
import { ref, onMounted } from 'vue';
import logo from '../assets/Logos/Logo White.svg';
import hamburger from '../assets/Icons/Menu White.svg';
import closeIcon from '../assets/Icons/Close White.svg';

const showSidebar = ref(false);

const navbarItems = [
  { name: 'HOME', path: '/' },
  { name: 'OUR SCREENS', path: '' },
  { name: 'SCHEDULE', path: '' },
  { name: 'MOVIE LIBRARY', path: '' },
  { name: 'LOCATION & CONTACT', path: '' },
  { name: 'GALLERY', path: '' },
];

const closeMenu = () => {
  showSidebar.value = false;
};

const handleBackdropClick = (e) => {
  if (e.target.id === 'backdrop') closeMenu();
};
</script>

<template>
  <div class="navbar">
    <!-- Logo -->
    <img :src="logo" alt="Logo" class="logo" />

    <!-- Desktop Menu -->
    <ul class="nav-items">
      <li v-for="item in navbarItems" :key="item.name">
        <h4 class="nav-link">{{ item.name }}</h4>
      </li>
    </ul>

    <!-- Hamburger Icon (mobile only) -->
    <img
      :src="hamburger"
      alt="Menu"
      class="hamburger"
      @click="showSidebar = true"
    />
  </div>

  <!-- Sidebar with backdrop -->
  <div
    v-if="showSidebar"
    id="backdrop"
    class="backdrop"
    @click="handleBackdropClick"
  >
    <div class="sidebar">
      <img
        :src="closeIcon"
        alt="Close"
        class="close-icon"
        @click="closeMenu"
      />

      <ul class="sidebar-items">
        <li v-for="item in navbarItems" :key="item.name">
          <h4 class="sidebar-link">{{ item.name }}</h4>
        </li>
      </ul>
    </div>
  </div>
</template>

<style scoped>
/* NAVBAR STYLES */
.navbar {
  background-color: black;
  padding: 2rem 10rem;
  display: flex;
  justify-content: space-between;
  align-items: center;
  color: grey;
  position: relative;
}

.logo {
  width: 150px;
}

.nav-items {
  list-style: none;
  display: flex;
  gap: 2rem;
}

.nav-link {
  cursor: pointer;
  transition: color 0.2s ease;
}

.nav-link:hover {
  color: white;
}

.hamburger {
  display: none;
  width: 32px;
  height: 32px;
  cursor: pointer;
}

/* SIDEBAR BACKDROP */
.backdrop {
  position: fixed;
  inset: 0;
  background-color: rgba(0, 0, 0, 0.4);
  backdrop-filter: blur(3px);
  z-index: 1000;
  display: flex;
  justify-content: flex-end;
}

/* SIDEBAR */
.sidebar {
  background-color: black;
  color: white;
  width: 50%;
  max-width: 300px;
  height: 100%;
  padding: 2rem 1.5rem;
  position: relative;
  animation: slide-in 0.3s ease-out;
  display: flex;
  flex-direction: column;
  gap: 2rem;
}

.sidebar-items {
  list-style: none;
  padding: 0;
  margin-top: 2rem;
}

.sidebar-link {
  font-size: 1.2rem;
  cursor: pointer;
  transition: color 0.2s ease;
}

.sidebar-link:hover {
  color: #ccc;
}

.close-icon {
  width: 24px;
  height: 24px;
  position: absolute;
  top: 1.2rem;
  right: 1.2rem;
  cursor: pointer;
}

/* SLIDE ANIMATION */
@keyframes slide-in {
  from {
    transform: translateX(100%);
  }
  to {
    transform: translateX(0%);
  }
}

/* RESPONSIVE BEHAVIOR */
@media (max-width: 1280px) {
  .nav-items {
    display: none;
  }

  .hamburger {
    display: block;
  }
}

@media (max-width: 1536px) {
  .navbar {
    padding: 2rem 2rem;
  }
}
</style>
