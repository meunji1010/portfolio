<template>
  <div>
    <HeaderOne @scrollToSection="handleScrollToSection" :isScrolled="isScrolled" />
    <div ref="sectionOne">
      <SectionOne />
    </div>
    <div ref="sectionTwo">
      <SectionTwo />
    </div>
    <div ref="sectionThree">
      <SectionThree />
    </div>
  </div>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from 'vue';
import HeaderOne from './components/HeaderOne.vue';
import SectionOne from './components/SectionOne.vue';
import SectionTwo from './components/SectionTwo.vue';
import SectionThree from './components/SectionThree.vue';

const isScrolled = ref(false);
const sectionOne = ref(null);
const sectionTwo = ref(null);
const sectionThree = ref(null);

const handleScroll = () => {
  isScrolled.value = window.scrollY > 50;
};

onMounted(() => {
  window.addEventListener("scroll", handleScroll);
});

onUnmounted(() => {
  window.removeEventListener("scroll", handleScroll);
});


const handleScrollToSection = (sectionName) => {
  let targetSection = null;

  if (sectionName === "ABOUT ME") targetSection = sectionOne.value;
  else if (sectionName === "CLONE CODING") targetSection = sectionTwo.value;
  else if (sectionName === "PUBLISHING") targetSection = sectionThree.value;

  if (targetSection) {
    targetSection.scrollIntoView({
      behavior: "smooth",
      block: "start"
    });
  }
};
</script>

<style scoped>
  
</style>