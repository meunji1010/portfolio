<template>
  <!-- CLONE CODING section -->
  <div class="section-two"  ref="sectionTwo">
    <h2 ref="title" class="section_title border_bottom fade-item" 
        :class="{ 'fade-in': isVisible.title }">
      CLONE CODING
    </h2>
    
    <div class="clone_wrap fade-item" ref="item0" :class="{ 'fade-in': isVisible.item0 }">
      <p class="clone_number number_one">01</p>
      <div class="clone_item">
        <a href="https://meunji1010.github.io/netflix/"><div class="netflix clone_img" :style="{backgroundImage: `url(${imgRef[0].images})`}"></div></a>
        <div class="clone_container">
          <p class="clone_name">Netflix Clone</p>
          <p class="clone_title">React 기반 웹 구현</p>
          <p class="clone_txt">React를 사용하여 Netflix의 주요 기능을 모방한<br>
          웹 애플리케이션을 개발하였습니다.<br>UI/UX 구현 능력을 강화하는 데 집중하였으며,<br> 
          비동기 데이터 처리와 동적 화면 구성을 통해<br> 
          효율적인 데이터 활용과 인터페이스 구현에 초점을 맞추었습니다.</p>
          <p>UI 디자인 방식 : Figma를 이용한 디자인 구축 후 코드 구현</p>
          <p>제작에 사용된 스킬 : React, React Router, TMdb API 연동</p>
          <p>레이아웃 제작 방식 : Flex 기반의 레이아웃</p>
          <p>플러그인 : Axios, react-slick, scss</p>
          <p>제작기간 : 2일</p>
          <p>제작 참여율 : 100%(개인프로젝트)<br>기획, UI디자인, 개발, 배포까지 전 과정 직접 수행</p>
          <p>배포방식 : GitHub</p>
          <a href="https://github.com/meunji1010/netflix"><button>GitHub 방문하기</button></a>
        </div>
      </div>
    </div>
    
    <div class="clone_wrap fade-item" ref="item1" :class="{ 'fade-in': isVisible.item1 }">
      <p class="clone_number number_two">02</p>
      <div class="clone_item">
      <div class="clone_container">
          <p class="clone_name">Tesla Clone</p>
          <p class="clone_title">HTML5 & CSS3 웹 표준 기반 구현</p>
          <p class="clone_txt">테슬라 웹사이트의 디자인과 인터랙션을 반영하여<br> 
          반응형 웹사이트를 구현했습니다. <br>웹 표준 및 접근성을 고려하며, <br>
          다양한 디바이스에서 최적의 사용자 경험(UX)을<br> 제공할 수 있도록 
          개발했습니다.  </p>
          <p>UI 디자인 방식 : Figma를 활용한 화면 분석 후, 클론 코딩 진행    </p>
          <p>제작에 사용된 스킬 : HTML5, CSS3</p>
          <p>레이아웃 제작 방식 : Flexbox를 활용한 구성</p>
          <p>제작기간 : 2일</p>
          <p>제작 참여율 : 100%(개인프로젝트)<br>기획, UI디자인, 개발, 배포까지 전 과정 직접 수행</p>
          <p>배포방식 : GitHub</p>
          <a href=""><button>GitHub 방문하기</button></a>
        </div>
        <a href="https://meunji1010.github.io/TESLA/index.html"><div class="tesla clone_img" :style="{backgroundImage: `url(${imgRef[1].images})`}"></div></a>
      </div>
    </div>

    
    <div class="clone_wrap fade-item" ref="item2" :class="{ 'fade-in': isVisible.item2 }">
      <p class="clone_number number_three">03</p>
      <div class="clone_item">
        <a href="https://meunji1010.github.io/AIRBNB/index.html"><div class="airbnb clone_img" :style="{backgroundImage: `url(${imgRef[2].images})`}"></div></a>
        <div class="clone_container">
          <p class="clone_name">Airbnb Clone</p>
          <p class="clone_title">반응형 숙박 예약 웹사이트</p>
          <p class="clone_txt">Airbnb 웹사이트의 디자인을 분석해<br> 
          실제 웹사이트의 UI 구성 구현하며,<br> 
          반응형 디자인을 적용하여 <br>다양한 화면 
          크기에서도 최적화 되게 설계되었습니다</p>
          <p>UI 디자인 방식 : Figma를 활용한 화면 분석 후, 클론 코딩 진행    </p>
          <p>제작에 사용된 스킬 : HTML5, CSS3</p>
          <p>레이아웃 제작 방식 : Flexbox를 활용한 구성</p>
          <p>제작기간 : 2일</p>
          <p>제작 참여율 : 100%(개인프로젝트)<br>기획, UI디자인, 개발, 배포까지 전 과정 직접 수행</p>
          <p>배포방식 : GitHub</p>
          <a href="https://github.com/meunji1010/meunji1010.github.io/tree/main/AIRBNB"><button>GitHub 방문하기</button></a>
        </div>
      </div>
    </div>

    
    <div class="clone_wrap fade-item" ref="item3" :class="{ 'fade-in': isVisible.item3 }">
      <p class="clone_number number_four">04</p>
      <div class="clone_item">
        <div class="clone_container">
          <p class="clone_name">Momentum Clone </p>
          <p class="clone_title">개인 맞춤 대시보드 웹페이지</p>
          <p class="clone_txt">사용자는 현재시간, 랜덤명언, 날씨정보, <br>할일목록 기능을 
          사용할 수 있으며,<br> 로컬스토리지를 활용한 데이터 저장 및 <br>
          사용자 맞춤형으로 개발하였습니다</p>
          <p>UI 디자인 방식 : Photoshop를 활용한 화면 분석 후, 클론 코딩 진행</p>
          <p>제작에 사용된 스킬 :  HTML5, CSS3, ES6,<br> OpenWeather API연동, LocalStorage 활용</p>
          <p>레이아웃 제작 방식 : Position과 Flexbox를 활용한 구성</p>
          <p>플러그인 : Axios 를 이용한 API 데이터 요청 및 응답 처리</p>
          <p>제작기간 : 2일</p>
          <p>제작 참여율 : 100%(개인프로젝트)<br>기획, UI디자인, 개발, 배포까지 전 과정 직접 수행</p>
          <p>배포방식 : GitHub</p>
          <a href="https://github.com/meunji1010/meunji1010.github.io/tree/main/momentum"><button>GitHub 방문하기</button></a>
          <p></p>
        </div>
        <a href="https://meunji1010.github.io/momentum/index.html"><div class="momentum clone_img" :style="{backgroundImage: `url(${imgRef[3].images})`}"></div></a>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from 'vue';

const imgRef = ref([
  {id:1, images:"./images/netflix_clone.webp"},
  {id:2, images:"./images/tesla_clone.webp"},
  {id:3, images:"./images/airbnb_clone.webp"},
  {id:4, images:"./images/momentum_clone.webp"}
]);
// 요소별 상태 관리
const isVisible = ref({
  title: false,
  item0: false,
  item1: false,
  item2: false,
  item3: false,
});

// 각 요소에 대한 ref
const title = ref(null);
const item0 = ref(null);
const item1 = ref(null);
const item2 = ref(null);
const item3 = ref(null);

const sectionTwo = ref(null);

const handleScroll = () => {
  const windowHeight = window.innerHeight;

  if (title.value) {
    const titleTop = title.value.getBoundingClientRect().top;
    if (titleTop < windowHeight * 0.8 && titleTop > 0) {
      isVisible.value.title = true;
    } else {
      isVisible.value.title = false;
    }
  }

  [item0, item1, item2, item3].forEach((item, index) => {
    if (item.value) {
      const itemTop = item.value.getBoundingClientRect().top;
      const itemBottom = item.value.getBoundingClientRect().bottom;

      if (itemTop < windowHeight * 0.8 && itemBottom > 0) {
        isVisible.value[`item${index}`] = true;
      } else {
        isVisible.value[`item${index}`] = false;
      }
    }
  });
};

onMounted(() => {
  window.addEventListener("scroll", handleScroll);
  handleScroll(); // 페이지 로드 시 체크
});

onUnmounted(() => {
  window.removeEventListener("scroll", handleScroll);
});
</script>


<style scoped>

  /* 섹션전체화면 */
  .section-two{
    width: 100%;
    font-family: 'TheJamsil3Regular';
    padding: 50px 20px;
    position: relative;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    margin-bottom: 200px;
  }
  /* 섹션 제목 */
  .section-two > h2{
    font-size: 80px;
    text-align: right;
    margin-bottom: 3rem;
  }
  /* 클론넘버 */
  .clone_number{
    font-size: 4.5rem;
    margin: 2rem;
    color: #92c6ff;
  }
  p.number_one,p.number_three{
    align-self: flex-end;
    margin-right: 20%;
  }
  /* 클론 이미지 */
  .section-two .clone_item >a{
    display: block;
    width: 650px;
    height: 400px;
  }
  .section-two a > div{
    width: 100%;
    height: 100%;
    border-radius: 20px;
  }
  .clone_img{
    background-size: cover;
    background-repeat: no-repeat;
  }
  
  /* 클론이름 */
  .clone_wrap{
    width: 100%;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    gap: 30px;
  }
  .clone_item{
    display: flex;
    justify-content: center;
    align-items: center;
  }

  /* 클론설명 */
  .clone_container{
    margin: 30px;
    background-color: #666;
    padding: 20px;
    border-radius: 10px;
  }
  .clone_container a{
    text-align: center;
    display: block;
    width: 400px;
  }
    .clone_container > p{
    font-size: 16px;
    display: flex;
    flex-direction: column;
  }
  p.clone_name{
    border-bottom: 1px solid #92c6ff;
    width: 50%;
    padding-bottom: 10px;
    margin-bottom: 10px;
    font-size: 30px;
  }
  p.clone_title{
    margin-bottom: 10px;
    font-size: 28px;
  }
  .clone_txt{
    font-family: 'TheJamsil2Light';
    font-size: 16px;
    line-height: 22px;
    margin-bottom: 1rem;
  }
  /* github방문 버튼 */
  .clone_container > a{
    width: 100%;
    height: 40px;
    display: flex;
    justify-content: center;
    margin-top: 20px;
  }
  .clone_container > a > button {
    background-color: #92c6ff;
    justify-content: center;
    border: none;
    border-radius: 10px;
    padding: 0 20px;
    color: #333;
    font-weight: bold;
    cursor: pointer;
  }
  /* 2~4번까지 설명*/
  p.number_one, p.number_three{
    margin-right: 25%;
  }
  p.number_two, p.number_four{
    align-self: first baseline;
    margin-left: 25%;
  }
  
  .section-two{
    background-size: cover;
  }
  /* 애니메이션 */
.fade-item {
  opacity: 0;
  transform: translateY(50px);
  transition: opacity 0.8s ease-out, transform 0.8s ease-out;
}

.fade-in {
  opacity: 1 !important;
  transform: translateY(0);
}
  /* 반응형 테블릿 */
  @media all and (max-width:1023px) { 
    .section-two .clone_number{
      align-self: center;
      margin: 20px;
    }
  } 
  /* 반응형 모바일 */
  @media all and (max-width:767px) {
    .section-two{
      padding: 0;
    }
    .section-two h2{
      font-size: 50px;
      text-align: center;
    }
    .section-two .clone_number{
      align-self: center;
      margin: 20px;
      font-size: 3.5rem;
    }
    .clone_item {
      display: flex;
      flex-direction: column; 
    }
    .clone_wrap:nth-of-type(2) .clone_item,
    .clone_wrap:nth-of-type(4) .clone_item {
      flex-direction: column-reverse;
    }
    p.clone_name, p.clone_title{
      align-self: center;
      text-align: center;
      width: 100%;
    }
    p.clone_txt{
    text-align: center;
  }
  }
  /* 반응형 모바일 min */
@media all and (max-width:479px) {
  .section-two{
    margin-bottom: 150px;
  }
  .section-two .clone_item > a{
    width: 380px;
    height: 200px;
  }
  h2.section_title{
    padding: 10px;
    font-size: 40px;
  }
}

</style>