<template>
  <div class="social-sidebar">
    <a href="https://github.com/yourusername" target="_blank" class="social-icon" title="GitHub">
      <GithubIcon :size="20" />
    </a>
    
    <a href="https://linkedin.com/in/yourusername" target="_blank" class="social-icon" title="LinkedIn">
      <LinkedinIcon :size="20" />
    </a>
    
    <a href="mailto:your@email.com" class="social-icon" title="Email">
      <MailIcon :size="20" />
    </a>

    <a href="https://fiverr.com/yourusername" target="_blank" class="social-icon fiverr" title="Fiverr">
      <span class="fiverr-text">fi</span>
    </a>
  </div>
</template>

<script setup lang="ts">
import { GithubIcon, LinkedinIcon, MailIcon } from 'lucide-vue-next';
</script>

<style scoped>
.social-sidebar {
  position: fixed;
  right: 2rem;
  top: 50%;
  transform: translateY(-50%);
  display: flex;
  flex-direction: column;
  gap: 1rem;
  z-index: 100; /* Ensure it stays above other content */
}

.social-icon {
  width: 45px;
  height: 45px;
  display: flex;
  align-items: center;
  justify-content: center;
  border-radius: 50%;
  border: 1px solid rgba(255, 255, 255, 0.1);
  background: rgba(15, 17, 21, 0.8);
  color: #94a3b8;
  text-decoration: none;
  transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
  backdrop-filter: blur(4px);
}

.social-icon:hover {
  border-color: #10b981;
  color: #10b981;
  transform: translateX(-5px); /* Gentle slide-out effect */
  box-shadow: 0 0 15px rgba(16, 185, 129, 0.2);
}

.fiverr-text {
  font-family: 'Inter', sans-serif;
  font-weight: 900;
  font-size: 0.9rem;
  letter-spacing: -1px;
}

/* Specific hover for Fiverr brand color if you want it */
.social-icon.fiverr:hover {
  border-color: #1dbf73;
  color: #1dbf73;
  box-shadow: 0 0 15px rgba(29, 191, 115, 0.2);
}

/* Hide on small mobile screens to prevent overlap with content */
@media (max-width: 768px) {
  .social-sidebar {
    display: none;
  }
}
</style>