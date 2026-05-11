<template>
  <nav class="navbar navbar-permanent-float">
    <div class="logo">AC</div>

    <div class="nav-links">
      <a 
        v-for="link in navLinks" 
        :key="link.id"
        href="javascript:void(0)"
        @click="handleNavClick(link.id)"
        :class="['nav-item', { 'active': activeSection === link.id }]"
      >
        {{ link.name }}
      </a>
    </div>

    <div class="actions">
      <button class="theme-toggle">
        <span class="moon-icon">🌙</span>
      </button>
      <a 
        href="/cv.pdf" 
        download="cv.pdf" 
        class="cv-button"
        >
        <span class="download-icon">↓</span> Download CV
      </a>
    </div>
  </nav>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from 'vue';

const emit = defineEmits(['scroll-to-home', 'scroll-to-aboutme', 'scroll-to-projects', 'scroll-to-experience', 'scroll-to-contact']);

const activeSection = ref('home');

const navLinks = [
  { name: 'Home', id: 'home', emit: 'scroll-to-home' },
  { name: 'About Me', id: 'aboutme', emit: 'scroll-to-aboutme' },
  { name: 'Projects', id: 'projects', emit: 'scroll-to-projects' },
  { name: 'Experiences', id: 'experience', emit: 'scroll-to-experience' },
  { name: 'Contact', id: 'contact', emit: 'scroll-to-contact' }
];

const handleNavClick = (id) => {
  const link = navLinks.find(l => l.id === id);
  if (link) {
    emit(link.emit);
    activeSection.value = id;
  }
};

let observer;

onMounted(() => {
  // Intersection Observer to handle active link white highlighting
  observer = new IntersectionObserver((entries) => {
    entries.forEach((entry) => {
      if (entry.isIntersecting) {
        activeSection.value = entry.target.id;
      }
    });
  }, { 
    threshold: 0.4,
    rootMargin: "-100px 0px -20% 0px" 
  });

  navLinks.forEach((link) => {
    const el = document.getElementById(link.id);
    if (el) observer.observe(el);
  });
});

onUnmounted(() => {
  if (observer) observer.disconnect();
});
</script>

<style scoped>
.navbar {
  position: sticky;
  z-index: 1000;
  display: flex;
  justify-content: space-between;
  align-items: center;
  transition: all 0.4s cubic-bezier(0.4, 0, 0.2, 1);
  box-sizing: border-box;

  /* Permanent Floating Styles */
  top: 20px; /* Distance from top edge */
  width: 90%;
  max-width: 1200px;
  margin: 0 auto;
  border-radius: 50px;
  background-color: rgba(15, 17, 21, 0.7); /* Translucent background */
  backdrop-filter: blur(12px); /* Glassmorphism */
  border: 1px solid rgba(255, 255, 255, 0.1);
  padding: 0.8rem 4%;
  box-shadow: 0 10px 30px rgba(0, 0, 0, 0.5);
}

.logo {
  font-size: 1.4rem;
  font-weight: 800;
  letter-spacing: -1px;
}

.nav-links {
  display: flex;
  gap: 2rem;
}

.nav-item {
  color: #94a3b8;
  text-decoration: none;
  font-size: 0.9rem;
  font-family: 'JetBrains Mono', monospace;
  transition: all 0.3s ease;
  padding-bottom: 2px;
  border-bottom: 2px solid transparent;
  cursor: pointer;
}

/* White highlight for the section you are on */
.nav-item.active {
  color: #ffffff;
  border-bottom: 2px solid #ffffff;
}

.nav-item:hover {
  color: #ffffff;
}

.actions {
  display: flex;
  align-items: center;
  gap: 1rem;
}

.cv-button {
  background-color: #ffffff;
  color: #000000;
  padding: 0.5rem 1.2rem;
  border-radius: 50px;
  font-size: 0.85rem;
  font-weight: 700;
  text-decoration: none;
  display: flex;
  align-items: center;
  gap: 0.5rem;
  transition: transform 0.2s ease;
}

.cv-button:hover {
  transform: translateY(-2px);
  background-color: #f0f0f0;
}

.theme-toggle {
  background: none;
  border: 1px solid rgba(255, 255, 255, 0.1);
  border-radius: 50%;
  padding: 6px;
  cursor: pointer;
  display: flex;
  align-items: center;
}

/* Ensure your page has enough padding at the top so the floating bar 
   doesn't overlap your Splashpage content initially */
</style>