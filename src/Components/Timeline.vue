<template>
  <section class="timeline-section">
    <h2 class="section-title">Development Journey<span>.</span></h2>

    <div class="timeline-container">
      <div class="line"></div>

      <div v-for="(item, index) in timeline" :key="index" class="timeline-item">
        <div class="node"></div>

        <div class="content-wrapper">
          <div class="image-container">
            <img :src="item.image" :alt="item.title" />
          </div>

          <div class="text-content">
            <span class="year">#{{ item.year }}</span>
            <h3 class="project-title">{{ item.title }}</h3>
            <p class="description">{{ item.description }}</p>
            
            <div class="tech-tags">
              <span v-for="tag in item.tech" :key="tag" class="tag">{{ tag }}</span>
            </div>

            <div class="links">
              <a v-if="item.link" :href="item.link" class="btn-live">Live Demo</a>
              <a :href="item.github" class="btn-git">GitHub</a>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup lang="ts">
import { timeline } from '../data/timeline';
</script>

<style scoped>
.timeline-section {
  padding: 4rem 10%;
  color: white;
}

.section-title {
  font-family: 'JetBrains Mono', monospace;
  font-size: 2.5rem;
  margin-bottom: 4rem;
}

.section-title span { color: #10b981; }

.timeline-container {
  position: relative;
  display: flex;
  flex-direction: column;
  gap: 5rem;
}

/* The Vertical Line */
.line {
  position: absolute;
  left: 7px; /* Positioned behind the nodes */
  top: 0;
  bottom: 0;
  width: 2px;
  background: linear-gradient(to bottom, #10b981, #1e293b);
  opacity: 0.3;
}

.timeline-item {
  position: relative;
  display: flex;
  padding-left: 40px; /* Space for the line/node */
}

.node {
  position: absolute;
  left: 0;
  top: 10px;
  width: 16px;
  height: 16px;
  background: #0c0e12;
  border: 2px solid #10b981;
  border-radius: 50%;
  z-index: 2;
}

.content-wrapper {
  display: grid;
  grid-template-columns: 1.2fr 1fr; /* Image left, text right */
  gap: 3rem;
  align-items: center;
}

.image-container img {
  width: 100%;
  border-radius: 12px;
  border: 1px solid rgba(255, 255, 255, 0.1);
}

.year {
  font-family: 'JetBrains Mono', monospace;
  color: #10b981;
  font-size: 2rem;
  opacity: 0.4;
  font-weight: 800;
}

.project-title {
  font-size: 1.8rem;
  margin: 0.5rem 0;
}

.description {
  color: #94a3b8;
  line-height: 1.6;
  margin-bottom: 1.5rem;
}

.tech-tags {
  display: flex;
  flex-wrap: wrap;
  gap: 0.5rem;
  margin-bottom: 2rem;
}

.tag {
  background: #1e293b;
  padding: 4px 12px;
  border-radius: 20px;
  font-size: 0.8rem;
  color: #e2e8f0;
}

.links {
  display: flex;
  gap: 1rem;
}

.btn-live, .btn-git {
  padding: 0.6rem 1.5rem;
  border-radius: 50px;
  text-decoration: none;
  font-weight: 600;
  font-size: 0.9rem;
  transition: 0.3s;
}

.btn-live { background: white; color: black; }
.btn-git { border: 1px solid #334155; color: white; }

.btn-live:hover { transform: translateY(-3px); box-shadow: 0 5px 15px rgba(255,255,255,0.2); }

/* Mobile View: Stack them vertically */
@media (max-width: 900px) {
  .content-wrapper { grid-template-columns: 1fr; }
}
</style>