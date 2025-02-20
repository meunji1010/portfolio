<template>
  <div>
    <HeaderOne @scrollToSection="handleScrollToSection" :isScrolled="isScrolled" />
    <div ref="sectionOne">
      <SectionOne />
    </div>
    <div ref="sectionTwo">
      <SectionTwo />
    </div>
    <!-- <div ref="publishing">
      <Publishing />
    </div> -->
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
import Publishing from './components/Publishing.vue';

const isScrolled = ref(false);
const sectionOne = ref(null);
const sectionTwo = ref(null);
const publishing = ref(null);
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
  let offset = 0; // 기본값

  if (sectionName === "ABOUT ME") {
    targetSection = sectionOne.value;
    offset = 150; 
  } else if (sectionName === "CLONE CODING") {
    targetSection = sectionTwo.value;
    offset = 100; 
  } else if (sectionName === "PUBLISHING") {
    targetSection = publishing.value;
    offset = 0; 
  } else if (sectionName === "ETC") {
    targetSection = sectionThree.value;
    offset = 0; 
  }

  if (targetSection) {
    const top = targetSection.getBoundingClientRect().top + window.scrollY - offset;
    window.scrollTo({ top, behavior: "smooth" });
  }
};
</script>

<style scoped>
  
</style>