<script setup lang="ts">
import { ref } from 'vue'
import Navbar from "./Components/Navbar.vue";
import Splashpage from "./Components/Splashpage.vue";
import AboutMe from "./Components/AboutMe.vue";
import Timeline from './Components/Timeline.vue';
import Experience from './Components/Experience.vue';
import Contact from './Components/Contact.vue';
import ScrollLinks from './Components/ScrollLinks.vue';

const aboutMe = ref<HTMLElement | null>(null)
const projects = ref<HTMLElement | null>(null)
const experience = ref<HTMLElement | null>(null)
const contact = ref<HTMLElement | null>(null)
const home = ref<HTMLElement | null>(null)
const scrollToHome = () => {
  home.value?.scrollIntoView({ behavior: 'smooth' })
}
const scrollToAboutMe = () => {
  aboutMe.value?.scrollIntoView({ behavior: 'smooth' })
}
const scrollToProjects = () => {
  projects.value?.scrollIntoView({ behavior: 'smooth' })
}
const scrollToExperience = () => {
  experience.value?.scrollIntoView({ behavior: 'smooth' })
}
const scrollToContact = () => {
  contact.value?.scrollIntoView({ behavior: 'smooth' })
}

</script>

<template>
  <Navbar 
    @scroll-to-home="scrollToHome" 
    @scroll-to-aboutme="scrollToAboutMe" 
    @scroll-to-projects="scrollToProjects" 
    @scroll-to-experience="scrollToExperience" 
    @scroll-to-contact="scrollToContact" 
  />
  <ScrollLinks/>

  <div class="container" id="home" ref="home">
    <Splashpage @scroll-to-content="scrollToAboutMe" />
  </div>

  <div class="container" id="aboutme" ref="aboutMe">
    <AboutMe />
  </div>
  
  <div class="container" id="projects" ref="projects">
    <Timeline />
  </div>

  <div class="container" id="experience" ref="experience">
    <Experience/>
  </div>

  <div class="container" id="contact" ref="contact">
    <Contact />
  </div>
</template>

<style>
/* Global styles stay the same */
body {
  margin: 0;
  padding: 0;
  background-color: #0c0e12;
  color: #ffffff;
  font-family: 'Inter', sans-serif;
  overflow-x: hidden; /* Prevents unwanted horizontal scroll from animations */
}

.container {
  padding: 2rem 10%;
}
</style>