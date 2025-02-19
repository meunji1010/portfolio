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
          10년 넘게 한 가지 일에 몰두하며 책임감을 키워온 저는, 이제 프론트엔드 개발자로 새로운 도전을 시작합니다.<br>
          코드가 언어처럼 소통의 도구라는 점에서 깊은 유대감을 느끼고, 끊임없이 성장하고 있습니다.<br>
          사용자 경험을 고려한 직관적인 UI 개발과 끈기를 바탕으로 문제를 끝까지 해결하는 힘이 저의 가장 큰 강점입니다.
        </p>
      </section>
      
    </div>

    <!-- 오른쪽 프로필 이미지 -->
    <div class="image-box">사진</div>
  </div>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from 'vue';

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
}
.section_title {
  font-size: 80px;
  align-self: flex-start;
}

/* INTRO & SKILLS 컨테이너 */
.intro {
  display: flex;
  justify-content: space-between;
  border-bottom: 2px solid white;
  padding-bottom: 20px;
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
  border-top: 2px solid #fff;
  padding-top: 10px;
  padding-bottom: 10px;
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
  width: 200px;
  height: 250px;
  background-color: #444;
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
      width: 100%;
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
}
</style>