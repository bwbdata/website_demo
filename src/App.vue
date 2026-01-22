<script setup lang="ts">
import { ref, onMounted } from 'vue'
import Navbar from './components/Navbar.vue'

const theme = ref<'light' | 'dark'>('light')

onMounted(() => {
  const savedTheme = localStorage.getItem('theme') as 'light' | 'dark' | null
  if (savedTheme) {
    theme.value = savedTheme
    document.documentElement.setAttribute('data-theme', savedTheme)
  } else if (window.matchMedia('(prefers-color-scheme: dark)').matches) {
    theme.value = 'dark'
    document.documentElement.setAttribute('data-theme', 'dark')
  }
})

const toggleTheme = () => {
  theme.value = theme.value === 'light' ? 'dark' : 'light'
  document.documentElement.setAttribute('data-theme', theme.value)
  localStorage.setItem('theme', theme.value)
}
</script>

<template>
  <div id="app">
    <Navbar :theme="theme" @toggle-theme="toggleTheme" />
    <router-view />
  </div>
</template>

<style scoped>
#app {
  min-height: 100vh;
}
</style>
