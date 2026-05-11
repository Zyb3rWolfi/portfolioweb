<template>
  <div class="tech-wall-container">
    <h2 class="title">My Tech Stack.</h2>

    <div class="marquee">
      <div class="marquee-content row-1">
        <div v-for="i in 4" :key="'a'+i" class="stack-list">
          <div 
            v-for="tech in row1" 
            :key="tech.name" 
            class="tech-badge"
            :style="{ borderColor: tech.color + '44', color: tech.color }"
          >
            <img :src="tech.icon" :alt="tech.name" class="tech-icon" />
            <span>{{ tech.name }}</span>
          </div>
        </div>
      </div>
    </div>

    <div class="marquee">
      <div class="marquee-content row-2">
        <div v-for="i in 4" :key="'b'+i" class="stack-list">
          <div 
            v-for="tech in row2" 
            :key="tech.name" 
            class="tech-badge"
            :style="{ borderColor: tech.color + '44', color: tech.color }"
          >
            <img :src="tech.icon" :alt="tech.name" class="tech-icon" />
            <span>{{ tech.name }}</span>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
const row1 = [
  { name: 'Vue.js', icon: '/icons/vuedotjs.svg', color: '#42b883' },
  { name: 'TypeScript', icon: '/icons/typescript.svg', color: '#3178c6' },
  { name: 'Node.js', icon: '/icons/nodedotjs.svg', color: '#339933' },
  { name: 'PostgreSQL', icon: '/icons/postgresql.svg', color: '#4169e1' },
  { name: 'Docker', icon: '/icons/docker.svg', color: '#2496ed' },
  { name: 'Git', icon: '/icons/git.svg', color: '#f05032' },
];

const row2 = [
  { name: 'C', icon: '/icons/c.svg', color: '#a8b9cc' },
  { name: 'C++', icon: '/icons/cplusplus.svg', color: '#00599c' },
  { name: 'Python', icon: '/icons/python.svg', color: '#3776ab' },
  { name: 'Laravel', icon: '/icons/laravel.svg', color: '#ff2d20' },
  { name: 'Dotnet', icon: '/icons/dotnet.svg', color: '#512bd4' },
];
</script>

<style scoped>
.tech-wall-container {
  padding: 3rem 0;
  overflow: hidden;
  display: flex;
  flex-direction: column;
  gap: 1.5rem; /* Slightly wider gap between rows */
}

.title {
  text-align: center;
  font-family: 'JetBrains Mono', monospace;
  margin-bottom: 2rem;
  font-size: 1.5rem;
  color: #ffffff;
}

.marquee {
  display: flex;
  width: 100%;
  mask-image: linear-gradient(
    to right,
    transparent,
    black 15%,
    black 85%,
    transparent
  );
}

.marquee-content {
  display: flex;
  gap: 0.75rem;
  width: max-content;
}

.row-1 {
  animation: scrollLeft 35s linear infinite;
}

.row-2 {
  animation: scrollRight 35s linear infinite;
}

.stack-list {
  display: flex;
  gap: 0.75rem;
  width: max-content;
}

.tech-badge {
  display: flex;
  align-items: center;
  gap: 0.6rem;
  background-color: #181d25; /* Darker background makes brand colors pop */
  padding: 0.5rem 1rem;
  border-radius: 8px;
  border: 1px solid; /* Color provided by :style */
  white-space: nowrap;
  font-family: 'JetBrains Mono', monospace;
  font-size: 0.85rem;
  transition: all 0.3s ease;
  box-shadow: 0 4px 6px -1px rgba(0, 0, 0, 0.1);
}

.tech-badge:hover {
  background-color: rgba(255, 255, 255, 0.05);
  transform: translateY(-3px);
  /* Uses the tech's own color for a glow effect on hover */
  box-shadow: 0 0 15px currentColor;
}

.tech-icon {
  width: 18px;
  height: 18px;
  object-fit: contain;
}

@keyframes scrollLeft {
  0% { transform: translateX(0); }
  100% { transform: translateX(-50%); }
}

@keyframes scrollRight {
  0% { transform: translateX(-50%); }
  100% { transform: translateX(0); }
}

.marquee:hover .marquee-content {
  animation-play-state: paused;
}
</style>