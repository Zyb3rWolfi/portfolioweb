<template>
  <section class="experience-section">
    <h2 class="title">Experience<span>.</span></h2>

    <div class="timeline">
      <div class="central-line"></div>

      <div 
        v-for="(exp, index) in experiences" 
        :key="index" 
        class="timeline-item"
        :class="index % 2 === 0 ? 'left' : 'right'"
      >
        <div class="dot"></div>

        <div class="card">
          <div class="card-header">
            <span class="company-icon">{{ exp.icon }}</span>
            <span class="company-name">{{ exp.company }}</span>
          </div>
          <h3 class="role">{{ exp.role }}</h3>
          <div class="duration">
            <span class="calendar-icon">📅</span> {{ exp.duration }}
          </div>
          <p class="description">{{ exp.description }}</p>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup lang="ts">
import { experiences } from '../data/timeline';
</script>

<style scoped>
.experience-section {
  padding: 5rem 10%;
  background-color: #0f1217;
}

.title {
  text-align: center;
  font-family: 'JetBrains Mono', monospace;
  font-size: 2.5rem;
  margin-bottom: 5rem;
}

.title span { color: #10b981; }

.timeline {
  position: relative;
  max-width: 1000px;
  margin: 0 auto;
}

.central-line {
  position: absolute;
  left: 50%;
  transform: translateX(-50%);
  width: 2px;
  height: 100%;
  background: rgba(255, 255, 255, 0.1);
}

.timeline-item {
  display: flex;
  justify-content: flex-end; /* Default for 'right' items */
  padding-left: 50px;
  width: 50%;
  margin-bottom: 2rem;
  position: relative;
}

/* Specific styling for 'left' items */
.timeline-item.left {
  align-self: flex-start;
  justify-content: flex-start;
  padding-left: 0;
  padding-right: 50px;
  left: 0;
}

/* Specific styling for 'right' items */
.timeline-item.right {
  align-self: flex-end;
  left: 50%;
}

.dot {
  position: absolute;
  width: 12px;
  height: 12px;
  background: #10b981;
  border-radius: 50%;
  top: 20px;
  z-index: 2;
}

.left .dot { right: -6px; }
.right .dot { left: -6px; }

.card {
  background: rgba(30, 41, 59, 0.3);
  border: 1px solid rgba(255, 255, 255, 0.05);
  border-radius: 12px;
  padding: 1.5rem;
  width: 100%;
  transition: transform 0.3s ease;
}

.card:hover {
  transform: translateY(-5px);
  border-color: #10b981;
}

.company-name {
  color: #10b981;
  font-family: 'JetBrains Mono', monospace;
  font-size: 0.9rem;
}

.role {
  margin: 0.5rem 0;
  font-size: 1.2rem;
}

.duration {
  font-size: 0.85rem;
  color: #94a3b8;
  margin-bottom: 1rem;
}

.description {
  font-size: 0.9rem;
  color: #cbd5e1;
  line-height: 1.6;
}

/* Mobile Responsiveness */
@media (max-width: 768px) {
  .central-line { left: 20px; }
  .timeline-item, .timeline-item.left, .timeline-item.right {
    width: 100%;
    left: 0;
    padding-left: 45px;
    padding-right: 0;
  }
  .dot { left: 14px !important; }
}
</style>