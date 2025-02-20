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
    background-color: #eee;
    padding: 10px;
  }
  li{
    cursor: pointer;
    margin: 10px;
    color: #888;
    transition: all 0.5s linear;
  }
  li:hover{
    color: #333;
  }
  .first{
    display: flex;
    flex-direction: column;
    margin: 200px 0;
  }
  @keyframes gradientMove {
  0% {
    background-position: 0% 50%;
  }
  50% {
    background-position: 100% 50%;
  }
  100% {
    background-position: 0% 50%;
  }
}
.first > h1 {
  font-family: 'SBAggroB';
  font-size: 128px;
  text-align: center;
  color: transparent;
  background: linear-gradient(90deg, #85FFBD, #FFFB7D, #78ace4);
  background-size: 200% 200%;
  -webkit-background-clip: text;
  background-clip: text;
  animation: gradientMove 6s infinite linear;
}
  .arrow{
    font-family: 'SBAggroB';
    font-size: 100px;
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
  @keyframes bounce {
  0%, 100% {
    /* transform: translateY(0); */
    transform: translate(-50%, 0);
  }
  50% {
    transform: translate(-50%, -20px);
  }
}
  .first > h1,
  .arrow{
    font-size: 50px;
  }
  .header{
    position: relative;
  }
  .header > .arrow{
    position: absolute;
    left: 50%;
    transform: translateX(-50%);
    bottom: 20%;
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