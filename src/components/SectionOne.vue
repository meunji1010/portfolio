<template>
  <!-- ABOUT ME section -->
  <div class="section-wrap">
    <div class="h2" ref="titleSection" :class="{ 'visible' : isVisible }">
      <h2 class="section_title border_bottom">ABOUT ME</h2>
    </div>
    <div ref="sectionOne" class="section-one" :class="{ 'visible': isVisible }">
    
      <!-- 텍스트 영역 -->
      <div class="text-content">
        
        <section class="intro">
          <div class="info">
            <h3>INTRODUCE</h3>
            <ul>
              <li><span>Name :</span> 심은지</li>
              <li><span>Phone :</span> 010-6245-4127</li>
              <li><span>Email :</span> meunji1010@gmail.com</li>
            </ul>
          </div>
          <section class="who-am-i">
          <h3>WHO AM I</h3>
          <p>
            10년 넘게 한 가지 일에 몰두하며 책임감을 키워온 저는, 이제 프론트엔드 개발자로 새로운 도전을 시작합니다.<br>
            코드가 언어처럼 소통의 도구라는 점에서 깊은 유대감을 느끼고, 끊임없이 성장하고 있습니다.<br>
            사용자 경험을 고려한 직관적인 UI 개발과 끈기를 바탕으로 문제를 끝까지 해결하는 힘이 저의 가장 큰 강점입니다.
          </p>
        </section>

        </section>
        
        
        
      </div>
      <div class="image-box" :style="{backgroundImage: `url(${img[0].img})`}"></div>
    </div>
    <div class="skills">
            <h3>SKILLS</h3>
            <ul>
              <li :style="{backgroundImage: `url(${icon[0].img})`}"></li>
              <li :style="{backgroundImage: `url(${icon[1].img})`}"></li>
              <li :style="{backgroundImage: `url(${icon[2].img})`}"></li>
              <li :style="{backgroundImage: `url(${icon[3].img})`}"></li>
              <li :style="{backgroundImage: `url(${icon[4].img})`}"></li>
              <li :style="{backgroundImage: `url(${icon[5].img})`}"></li>
              <li :style="{backgroundImage: `url(${icon[6].img})`}"></li>
            </ul>
          </div>
  </div>
</template>

<script setup>

import { ref, onMounted, onUnmounted } from 'vue';

const icon = ref([
  {id:1, img:"./images/HTML5.svg"},
  {id:2, img:"./images/CSS.svg"},
  {id:3, img:"./images/JavaScript.svg"},
  {id:4, img:"./images/photoshop.png"},
  {id:5, img:"./images/Illustrator.svg"},
  {id:6, img:"./images/React.svg"},
  {id:7, img:"./images/Vue.png"}
]);
const img = ref([{id:1, img:"./images/me.jpg"}])
const sectionOne = ref(null);
const titleSection = ref(null);
const isVisible = ref(false);

const handleScroll = () => {
  if (sectionOne.value || titleSection.value) {
    const rect1 = sectionOne.value.getBoundingClientRect();
    const rect2 = titleSection.value.getBoundingClientRect();
    
    
    isVisible.value = rect1.top < window.innerHeight * 0.75 || rect2.top < window.innerHeight * 0.75;
  }
};

onMounted(() => {
  window.addEventListener("scroll", handleScroll);
  handleScroll();
});

onUnmounted(() => {
  window.removeEventListener("scroll", handleScroll);
});
</script>


<style scoped>
.section-wrap{
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}
.section-one {
  font-family: 'TheJamsil3Regular';
  display: flex;
  justify-content: center;
  align-items: center;
  padding-top: 100px;
  opacity: 0;
  transform: translateY(50px); 
  transition: opacity 1.5s ease-out, transform 0.8s ease-out;
  gap: 20px;
}
.h2, .section-one {
  opacity: 0;
  transform: translateY(50px);
  transition: opacity 1.5s ease-out, transform 0.8s ease-out;
}

.h2.visible, .section-one.visible {
  opacity: 1;
  transform: translateY(0);
}

/* 왼쪽 텍스트 컨텐츠 */
.text-content {
  display: flex;
  flex-direction: column;
}

/* ABOUT ME 제목 */
.h2{
  display: flex;
  justify-content: center;
  width: 60%;
}
.section_title {
  font-size: 80px;
  align-self: center;
  text-align: center;
  width: 60%;
}

/* INTRO & SKILLS 컨테이너 */
.intro {
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  position: relative; /* 가상 요소 위치 설정 */
  padding-bottom: 20px;
}

.skills ul {
  display: flex;
}
.skills li{
  text-align: center;
  flex: 1;
}
.skills li:nth-child(5){
  grid-column: 2 / 4;
  text-align: left;
}

/* 기본 스타일 */
.skills li {
  font-size: 18px;
  font-weight: bold;
  text-transform: uppercase;
}
/* INTRO & SKILLS 개별 영역 */

.info {
  width: 100%;
  box-sizing: border-box;
  position: relative; /* 가상 요소 위치 조정 */
  padding: 10px 0;
}
.skills{
  width: 55%;
  box-sizing: border-box;
  position: relative;
  padding: 10px 0;
  padding-bottom: 100px;
}
.info::before, .skills::before {
  content: "";
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 2px; /* border-top 두께 */
  background: linear-gradient(90deg, #78ace4, #6f41b6); /* 그라디언트 적용 */
}


.info h3, .skills h3, .who-am-i h3 {
  font-size: 36px;
  margin-bottom: 10px;
}

.info ul, .skills ul {
  list-style: none;
  padding: 0;
}

.info li, .skills li {
  margin: 5px 0;
  font-size: 18px;
}
.skills li{
  width: 60px;
  height: 60px;
  background-repeat: no-repeat;
  background-size: contain;
}
/* WHO AM I */
.who-am-i {
  margin-top: 30px;
  width: 400px;
  position: relative;
  padding-top: 20px;
}
.who-am-i::before{
  content: "";
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 2px; /* border-top 두께 */
  background: linear-gradient(90deg, #78ace4, #6f41b6); /* 그라디언트 적용 */
}

.who-am-i p {
  font-size: 18px;
  line-height: 1.6;
}

/* 오른쪽 프로필 이미지 */
.profile-image {
  width: 30%;
  display: flex;
  justify-content: center;
  align-items: center;
}
.image-box {
  background-size: cover;
  width: 400px;
  height: 500px;
  
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 18px;
  color: white;
  margin: 20px;
}
  /* 반응형 테블릿 */
  @media all and (max-width:1023px) { 
    .section-one{
      flex-direction: column;
      justify-content: center;
      align-items: center;
      padding: 0;
    }
    .h2{
      align-items: center;
      justify-content: center;
      width: 100%;
    }
    h2.section_title{
      justify-content: center;
      align-items: center;
      text-align: center;
      align-self: center;
      order: -1;
    }
    .image-box{
      margin-top: 20px;
      order: 1;
    }
    .text-content{
      justify-content: center;
      align-items: center;
      order: 3;
    }
    .skills{
      width: 45%;
    }
    .skills li{
      width: 50px;
      height: 50px;
    }
  } 
  /* 반응형 모바일 */
  @media all and (max-width:767px) {
    .section-one{
      flex-direction: column;
      justify-content: center;
      align-items: center;
    }
    .h2{
      width: 100%;
    }
    h2.section_title{
      font-size: 50px;
      align-self:center;
    }
    .text-content{
      display: flex;
      flex-direction: column;
      justify-content: center;
      align-items: center;
      text-align: center;
      padding-bottom: 10%;
    }
    .intro{
      flex-direction: column;
      justify-content: center;
      align-items: center;
      width: 100%;
    }
    .info{
      width: 100%;
    }
    .info h3, .skills h3, .who-am-i h3 {
      font-size: 24px;
      margin-bottom: 10px;
    }
    .skills{
      width: 70%;
      gap: 10px;
    }
    .skills li{
      width: 50px;
      height: 50px;
    }
    .section-one li,
    .section-one p{
      font-size: 16px;
    }
    .image-box{
      width: 300px;
      height: 400px;
      margin-bottom: 10px;
    } 
    .skills > ul{
      display: flex;
      flex-wrap: wrap;
      justify-content: center;
      align-items: center;
    }
    .who-am-i > p{
      word-break: keep-all;
    }
  }
  /* 반응형 모바일 min */
@media all and (max-width:479px) {
  .section-one li,
  .section-one p{
    font-size: 12px;
  }
  .section-one span{
    font-size: 16px;
  }
  .image-box{
    width: 300px;
    height: 400px;
  }
  .skills{
    width: 400px;
  }
  .skills li{
    width: 30px;
    height: 30px;
  }
}
</style>