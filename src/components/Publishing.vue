<template>
  <div class="publishing">
    <h2 class="section_title border_bottom">WEBSITE PUBLISHING</h2>
    <div class="wrapper">
      <div class="image-box">
        <button class="prev-btn">&lt;</button>
        
      </div>
      <div class="explane">
        <h5>모바일 플래시카드 퀴즈</h5>
        <h4>React 기반의 학습 플랫폼</h4>
        <p>프로젝트 설명</p>
        <p>모바일 사용자 경험을 최적화한 UI/UX를 적용하여 <br>
          플래시카드 학습 웹 애플리케이션을 React 기반으로 개발하였습니다.</p>
        <p>UI 디자인 방식 : Figma를 활용하여 모바일 중심의 UX 디자인</p>
        <p>제작에 사용된 스킬 : React(Hooks, useState 활용)</p>
        <p>레이아웃 제작 방식 : Flexbox를 활용하여 UI 요소 정렬</p>
        <p>제작기간 : 1일</p>
        <p>제작 참여율 : 100%(개인프로젝트)<br>
          기획, UI 디자인, 개발, 배포까지 전 과정 직접 수행</p>
        <p>배포방식 : GitHub</p>
      </div>
      <button class="next-btn">&gt;</button>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue';

</script>

<style scoped>
.publishing{
  display: flex;
  flex-direction: column;
  justify-content: center;
}
h2{
  width: 80%;
  text-align: center;
}
.wrapper{
  display: flex;
}

</style>