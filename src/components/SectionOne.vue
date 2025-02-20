<template>
  <!-- ABOUT ME section -->
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

        <div class="skills">
          <h3>SKILLS</h3>
          <ul>
            <li>HTML</li>
            <li>CSS</li>
            <li>JS</li>
            <li>PHOTOSHOP</li>
            <li>ILLUSTRATOR</li>
            <li>REACT</li>
            <li>VUE</li>
          </ul>
        </div>
      </section>
      
      <section class="who-am-i">
        <h3>WHO AM I</h3>
        <p>
          10년 넘게 한 가지 일에 몰두하며 책임감을 키워온 저는, 이제 프론트엔드 개발자로서 새로운 도전을 시작합니다.<br>
          오랜 시간 한 분야에서 쌓아온 경험은 단순한 기술력뿐만 아니라,<br> 
          끈기와 문제 해결 능력, 그리고 책임감을 기르는 데 큰 밑바탕이 되었습니다.<br>
          웹 개발은 단순히 기능을 구현하는 것을 넘어,<br>
          사용자가 직관적으로 이해하고 편리하게 사용할 수 있는 UI/UX를 설계하는 과정이라고 생각합니다.<br>
          이러한 점에서 저는 코드 한 줄 한 줄에도 사용자의 경험을 최우선으로 고려하며 개발하고자 합니다.<br>
          앞으로도 더 나은 사용자 경험을 제공하는 개발자가 되기 위해 최신 기술을 배우고,<br>
          깊이 있는 고민을 지속하며, 협업하는 과정에서 더 큰 가치를 만들어 나가고자 합니다.
        </p>
      </section>
      
    </div>

    <!-- 오른쪽 프로필 이미지 -->
    <div class="image-box" :style="{backgroundImage: `url(${img[0].img})`}"></div>
  </div>
</template>

<script setup>

import { ref, onMounted, onUnmounted } from 'vue';

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
/* 전체 섹션 */
.section-one {
  font-family: 'TheJamsil3Regular';
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 50px 20px;
  opacity: 0;
  transform: translateY(50px); 
  transition: opacity 1.5s ease-out, transform 0.8s ease-out;
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
  width: 65%;
}

/* ABOUT ME 제목 */
.h2{
  display: flex;
  justify-content: center;
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
  justify-content: space-between;
  position: relative; /* 가상 요소 위치 설정 */
  padding-bottom: 20px;
}

.intro::after {
  content: "";
  position: absolute;
  bottom: 0;
  left: 0;
  width: 100%;
  height: 2px; /* border-bottom 두께 */
  background: linear-gradient(90deg, #78ace4, #6f41b6); /* 그라디언트 적용 */
}
.skills ul {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  grid-template-rows: auto auto auto; 
  gap: 15px;
  padding: 0;
  list-style: none;
  max-width: 400px;
}
.skills li{
  text-align: center;
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

.info, .skills {
  width: 45%;
  box-sizing: border-box;
  position: relative; /* 가상 요소 위치 조정 */
  padding-top: 10px;
  padding-bottom: 10px;
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

/* WHO AM I */
.who-am-i {
  margin-top: 30px;
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

  } 
  /* 반응형 모바일 */
  @media all and (max-width:767px) {
    .section-one{
      flex-direction: column;
      justify-content: center;
      align-items: center;
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
    .info, .skills{
      width: 100%;
    }
    .info h3, .skills h3, .who-am-i h3 {
      font-size: 24px;
      margin-bottom: 10px;
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
}
</style>