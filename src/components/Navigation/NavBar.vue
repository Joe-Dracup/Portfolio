<script setup lang="ts">
import { ref } from 'vue'
import NavLink from './NavLink.vue'
import ThemeToggler from './ThemeToggler.vue'

const showSubMenu = ref(false)

let navLinks = [
  { To: '/', Name: 'Home' },
  { To: '/about', Name: 'About' }
]
</script>

<template>
  <div class="nav-container">
    <ThemeToggler />
    <div>
      <a class="hamburger-icon-container" @click="showSubMenu = !showSubMenu">
        <svg
          class="hamburger-icon"
          xmlns="http://www.w3.org/2000/svg"
          fill="none"
          viewBox="0 0 24 24"
          strokeWidth="1.5"
          stroke="currentColor"
        >
          <path
            strokeLinecap="round"
            strokeLinejoin="round"
            d="M3.75 6.75h16.5M3.75 12h16.5m-16.5 5.25h16.5"
          />
        </svg>
      </a>
    </div>
  </div>
  <Transition name="slide">
    <div class="nav-item-container" v-if="showSubMenu">
      <NavLink
        v-for="nav in navLinks"
        @navigating="showSubMenu = false"
        :To="nav.To"
        :Name="nav.Name"
        :key="nav.To"
      />
    </div>
  </Transition>
</template>

<style scoped>
.nav-container {
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  padding: 1rem;
}

.hamburger-icon-container {
  display: flex;
  align-items: center;
}

.hamburger-icon {
  height: 2rem;
  width: 2rem;
}

.nav-item-container {
  display: flex;
  flex-direction: column;
}

.slide-enter-active,
.slide-leave-active {
  transition: all 0.25s ease-out;
}

.slide-enter-from {
  opacity: 0;
  transform: translateY(-30px);
}

.slide-leave-to {
  opacity: 0;
  transform: translateY(-30px);
}
</style>
./NavLink.vue./ThemeToggler.vue
