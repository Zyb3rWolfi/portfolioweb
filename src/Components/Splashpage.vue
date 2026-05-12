<template>
  <section class="hero">
    <div class="terminal-text">
      <h1 class="name">
        <span class="prompt">></span> Hi, I'm 
        <span class="highlight">Antons Cereskvics</span><span class="cursor">_</span>
      </h1>
      
      <p class="description">
        A 2nd year computer science student focused on building 
        <span class="tech-stack">Full-stack apps</span>,
        <span class="tech-stack">video games</span>, and
        <span class="tech-stack">Clean Architectures</span>.
      </p>
    </div>
    <button @click="$emit('scroll-to-content')" class="scroll-down">
      <span class="arrow">↓</span>
    </button>
  </section>
</template>

<script setup lang="ts">
defineEmits(['scroll-to-content'])
</script>

<style scoped>
.hero {
  position: relative; /* Essential for positioning the arrow */
  display: flex;
  flex-direction: column;
  justify-content: center;
  min-height: 90vh; /* Increased to fill more screen */
  padding: 0 10%;
}

/* 1. Typewriter Animation */
.name {
  font-family: 'JetBrains Mono', monospace;
  font-size: 2.5rem;
  margin-bottom: 1rem;
  overflow: hidden;
  white-space: nowrap;
  width: 0;
  animation: typing 2s steps(30, end) forwards;
}

.prompt {
  color: #10b981; /* Green "terminal" prompt color */
  margin-right: 10px;
}

.highlight {
  color: #fff;
}

/* 2. Blinking Cursor */
.cursor {
  display: inline-block;
  animation: blink 1s step-end infinite;
}

/* 3. Subtext Fade-in */
.description {
  font-family: 'IBM Plex Mono', monospace;
  font-size: 1.1rem;
  color: #94a3b8;
  max-width: 600px;
  line-height: 1.8;
  opacity: 0;
  animation: fadeIn 1s ease forwards;
  animation-delay: 2.2s; /* Waits for typing animation to finish */
}

.tech-stack {
  color: #e2e8f0;
  border-bottom: 1px dashed #475569;
}

/* Keyframes */
@keyframes typing {
  from { width: 0 }
  to { width: 100% }
}

@keyframes blink {
  from, to { opacity: 1 }
  50% { opacity: 0 }
}

@keyframes fadeIn {
  from { opacity: 0; transform: translateY(10px); }
  to { opacity: 1; transform: translateY(0); }
}
.scroll-down {
  position: absolute;
  bottom: 40px;
  left: 50%;
  transform: translateX(-50%);
  background: transparent;
  border: 1px solid #334155;
  color: #94a3b8;
  width: 45px;
  height: 45px;
  border-radius: 50%;
  cursor: pointer;
  display: flex;
  align-items: center;
  justify-content: center;
  animation: bounce 2s infinite;
  transition: all 0.3s ease;
}

.scroll-down:hover {
  border-color: #ffffff;
  color: #ffffff;
}

@keyframes bounce {
  0%, 20%, 50%, 80%, 100% { transform: translateX(-50%) translateY(0); }
  40% { transform: translateX(-50%) translateY(-10px); }
  60% { transform: translateX(-50%) translateY(-5px); }
}
@media (max-width: 768px) {
  .hero {
    padding: 0 5%; /* Give more room on the sides */
    min-height: 80vh; /* Prevent overlapping with the floating navbar */
  }

  .name {
    font-size: 1.8rem; /* Scale down the font */
    white-space: normal; /* CRITICAL: Allow text to wrap to next line */
    width: auto; /* Reset width for mobile */
    animation: fadeIn 1s ease forwards; /* Use fadeIn instead of typing */
  }

  /* Adjust the description for mobile */
  .description {
    font-size: 1rem;
    line-height: 1.6;
    animation-delay: 0.5s; /* Faster reveal on mobile */
  }

  /* Make the scroll arrow smaller so it doesn't hit the text */
  .scroll-down {
    bottom: 20px;
    width: 35px;
    height: 35px;
  }
}
</style>