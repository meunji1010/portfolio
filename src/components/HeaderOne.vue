<template>
  <div class="header">
    <header :class="{ 'scrolled': isScrolled }">
      <nav>
        <ul>
          <li v-for="(item, index) in menuItems" :key="index" @click="scrollToSection(item)">
            {{ item }}
          </li>
        </ul>
      </nav>
    </header>
    <div class="first">
      <h1>EUNJI'S<br>PORTFOLIO</h1>
    </div>
    <p class="arrow">∨</p>
  </div>
</template>

<script setup>
import { ref, defineProps } from 'vue';

defineProps({
  isScrolled: Boolean
});

const emit = defineEmits(["scrollToSection"]);

const menuItems = ref(["HOME", "ABOUT ME", "CLONE CODING", "PUBLISHING"]);

const scrollToSection = (item) => {
  if (item === "HOME") {
    window.scrollTo({
      top: 0,
      behavior: "smooth"
    });
  } else {
    emit("scrollToSection", item);
  }
};
</script>



<style scoped>
  .header{
    height: 80vh;
  }
  nav{
    font-family: 'TheJamsil5Bold';
    display: block;
    width: 100%;
    position: fixed;
    top: 0;
    right: 0;
    z-index: 2;
  }
  ul{
    display: flex;
    justify-content: flex-end;
    background-color: #333;
  }
  li{
    cursor: pointer;
    margin: 10px;
  }
  .first{
    display: flex;
    flex-direction: column;
    margin: 200px 0;
  }
  .first > h1,
  .arrow{
    font-family: 'SBAggroB';
    font-size: 128px;
    text-align: center;
  }

  /*** 화살표 애니메이션처리 */
  @keyframes bounce {
  0%, 100% {
    transform: translateY(0);
  }
  50% {
    transform: translateY(-20px);
  }
}
  .arrow{
    animation: bounce 1.5s infinite ease-in-out;
  }

  /* 반응형 테블릿 */
  @media all and (max-width:1023px) { 
  .first > h1,
  .arrow{
    font-size: 100px;
  }
} 
  /* 반응형 모바일 */
  @media all and (max-width:767px) {
    .first > h1,
  .arrow{
    font-size: 70px;
  }
  ul{
    justify-content: center;
  }
  li{
    font-size: 18px;
  }
}
/* 반응형 모바일 min */
@media all and (max-width:479px) {
  .first > h1,
  .arrow{
    font-size: 50px;
  }
  ul{
    width: 100%;
    display: flex;
    justify-content: center;
  }
  li{
    font-size: 12px;
  }
}
</style>