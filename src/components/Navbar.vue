<script setup lang="ts">
import { ref } from 'vue'
import { useRouter, useRoute } from 'vue-router'

interface Props {
  theme: 'light' | 'dark'
}

defineProps<Props>()
const emit = defineEmits<{
  toggleTheme: []
}>()

const router = useRouter()
const route = useRoute()
const mobileMenuOpen = ref(false)

const navItems = [
  { name: '首页', path: '/' },
  { name: '案例展示', path: '/portfolio' },
  { name: '关于我们', path: '/about' },
  { name: '联系我们', path: '/contact' },
  { name: '常见问题', path: '/faq' }
]

const toggleMobileMenu = () => {
  mobileMenuOpen.value = !mobileMenuOpen.value
}

const navigateTo = (path: string) => {
  router.push(path)
  mobileMenuOpen.value = false
}
</script>

<template>
  <nav class="navbar">
    <div class="container">
      <div class="nav-content">
        <div class="logo" @click="navigateTo('/')">
          <img src="/logo.png" alt="黑白蜂工作室" class="logo-image" />
          <div class="logo-text-wrapper">
            <span class="logo-text">黑白蜂工作室</span>
            <span class="logo-subtitle">Black & White Bee Studio</span>
          </div>
        </div>

        <div class="nav-links" :class="{ 'mobile-open': mobileMenuOpen }">
          <a
            v-for="item in navItems"
            :key="item.path"
            class="nav-link"
            :class="{ active: route.path === item.path }"
            @click="navigateTo(item.path)"
          >
            {{ item.name }}
          </a>
        </div>

        <div class="nav-actions">
          <button class="theme-toggle" @click="emit('toggleTheme')" aria-label="切换主题">
            <svg v-if="theme === 'light'" width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
              <path d="M21 12.79A9 9 0 1 1 11.21 3 7 7 0 0 0 21 12.79z"></path>
            </svg>
            <svg v-else width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
              <circle cx="12" cy="12" r="5"></circle>
              <line x1="12" y1="1" x2="12" y2="3"></line>
              <line x1="12" y1="21" x2="12" y2="23"></line>
              <line x1="4.22" y1="4.22" x2="5.64" y2="5.64"></line>
              <line x1="18.36" y1="18.36" x2="19.78" y2="19.78"></line>
              <line x1="1" y1="12" x2="3" y2="12"></line>
              <line x1="21" y1="12" x2="23" y2="12"></line>
              <line x1="4.22" y1="19.78" x2="5.64" y2="18.36"></line>
              <line x1="18.36" y1="5.64" x2="19.78" y2="4.22"></line>
            </svg>
          </button>

          <button class="mobile-menu-toggle" @click="toggleMobileMenu" aria-label="菜单">
            <svg v-if="!mobileMenuOpen" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
              <line x1="3" y1="12" x2="21" y2="12"></line>
              <line x1="3" y1="6" x2="21" y2="6"></line>
              <line x1="3" y1="18" x2="21" y2="18"></line>
            </svg>
            <svg v-else width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
              <line x1="18" y1="6" x2="6" y2="18"></line>
              <line x1="6" y1="6" x2="18" y2="18"></line>
            </svg>
          </button>
        </div>
      </div>
    </div>
  </nav>
</template>

<style scoped>
.navbar {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  z-index: 1000;
  background: var(--bg-card);
  border-bottom: 1px solid var(--border-color);
  backdrop-filter: blur(10px);
  box-shadow: var(--shadow-sm);
}

.nav-content {
  display: flex;
  align-items: center;
  justify-content: space-between;
  height: 70px;
}

.logo {
  display: flex;
  align-items: center;
  gap: 0.75rem;
  cursor: pointer;
  transition: transform 0.3s ease;
}

.logo:hover {
  transform: scale(1.05);
}

.logo-image {
  height: 45px;
  width: auto;
  object-fit: contain;
}

.logo-text-wrapper {
  display: flex;
  flex-direction: column;
}

.logo-text {
  font-size: 1.25rem;
  font-weight: 700;
  background: var(--accent-gradient);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
  line-height: 1.2;
}

.logo-subtitle {
  font-size: 0.7rem;
  color: var(--text-secondary);
  margin-top: 2px;
}

.nav-links {
  display: flex;
  gap: 2rem;
  align-items: center;
}

.nav-link {
  color: var(--text-secondary);
  text-decoration: none;
  font-weight: 500;
  transition: color 0.3s ease;
  cursor: pointer;
  position: relative;
}

.nav-link::after {
  content: '';
  position: absolute;
  bottom: -5px;
  left: 0;
  width: 0;
  height: 2px;
  background: var(--accent-gradient);
  transition: width 0.3s ease;
}

.nav-link:hover,
.nav-link.active {
  color: var(--accent-primary);
}

.nav-link.active::after {
  width: 100%;
}

.nav-actions {
  display: flex;
  gap: 1rem;
  align-items: center;
}

.theme-toggle {
  display: flex;
  align-items: center;
  justify-content: center;
  width: 40px;
  height: 40px;
  border-radius: 8px;
  background: var(--bg-secondary);
  border: none;
  color: var(--text-primary);
  cursor: pointer;
  transition: all 0.3s ease;
}

.theme-toggle:hover {
  background: var(--accent-primary);
  color: white;
  transform: rotate(15deg);
}

.mobile-menu-toggle {
  display: none;
  align-items: center;
  justify-content: center;
  width: 40px;
  height: 40px;
  border-radius: 8px;
  background: transparent;
  border: none;
  color: var(--text-primary);
  cursor: pointer;
}

@media (max-width: 768px) {
  .nav-links {
    position: fixed;
    top: 70px;
    left: 0;
    right: 0;
    flex-direction: column;
    background: var(--bg-card);
    border-bottom: 1px solid var(--border-color);
    padding: 1rem 0;
    gap: 0;
    transform: translateY(-100%);
    opacity: 0;
    visibility: hidden;
    transition: all 0.3s ease;
  }

  .nav-links.mobile-open {
    transform: translateY(0);
    opacity: 1;
    visibility: visible;
  }

  .nav-link {
    width: 100%;
    padding: 1rem 2rem;
    text-align: center;
  }

  .nav-link::after {
    display: none;
  }

  .mobile-menu-toggle {
    display: flex;
  }
}
</style>
