<template>
    <section class="about-me">
      <h2 class="title">About Me<span>.</span></h2>
      <p>
        Hi! I'm Antons Cereskevics, a Computer Science Undergraduate, i have a strong interest in building games and full-stack applications. I have experience with a variety of technologies, including JavaScript, TypeScript, Python, C#, and more. I'm passionate about learning new technologies and applying them to create innovative solutions.
        </p>
    <TechStack />

    </section>

</template>

<script setup lang="ts">
import TechStack from './TechStack.vue';
</script>
<style scoped>
.title span { color: #10b981; }

.about-me {
  padding: 2rem;
  background-color: #0f1217;
  border-radius: 8px;
  display: flex;
  flex-direction: column;
  justify-content: center;
  min-height: 90vh; /* Increased to fill more screen */
  padding: 0 10%;
}

.about-me h2 {
    font-family: 'JetBrains Mono', monospace;
  font-size: 2.5rem;
  margin-bottom: 0.5rem;
}

.about-me p {
  padding-left: 0%;
  font-family: 'JetBrains Mono', monospace;
  margin-bottom: 2rem;
  font-size: 1rem;
  color: #ffffff;
}

</style>