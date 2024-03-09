<script setup lang="ts">
import { ref } from 'vue'

// ToDo - fix flashbanging

const isDarkMode = ref(window.matchMedia('(prefers-color-scheme: dark)').matches)

setTheme()

function toggleTheme() {
  isDarkMode.value = !isDarkMode.value
  console.log(isDarkMode.value)
  setTheme()
}

function setTheme() {
  const theme = isDarkMode.value ? 'dark' : 'light'
  console.log(theme)
  document.documentElement.setAttribute('data-theme', theme)
}
</script>

<template>
  <a class="darkModeToggleContainer" @click="toggleTheme">
    <input type="checkbox" id="darkModeToggle" v-model="isDarkMode" />
  </a>
</template>

<style scoped>
@import '../../assets/variables.css';
.darkModeToggleContainer {
  display: flex;
  align-items: center;
}

#darkModeToggle {
  appearance: none;
  -webkit-appearance: none;
  -moz-appearance: none;
  width: 3rem;
  height: 1.5rem;
  border-radius: 1.5rem;
  background-color: var(--vt-c-black-soft);
  position: relative;
  transition: all 0.5s ease-in;
  cursor: pointer;
  z-index: 1;
}

#darkModeToggle::before {
  content: '';
  width: 1.125rem;
  height: 1.125rem;
  border-radius: 50%;
  background: var(--vt-c-white-soft);
  position: absolute;
  top: 50%;
  left: 8%;
  transform: translateY(-50%);
  transition: all 0.3s ease-in;
}

#darkModeToggle:checked {
  background: var(--vt-c-white-soft);
}

#darkModeToggle:checked::before {
  background: var(--vt-c-black-soft);
  left: 55%;
}
</style>
