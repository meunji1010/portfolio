<template>
  <!-- practical publishing section -->
  <div class="section_three" :class="{'visible' : isVisible}" ref="sectionThree" >
    <h2 class="section_title border_bottom">PRACTICAL PUBLISHING</h2>
    <div class="menu">
      <ul>
        <li 
            v-for="item in items" 
            :key="item.id"
            @click="selectedCategory(item.name)"  
            :class="{ active: selectedMenu === item.name }" 
            class="menu-item"
        >
  {{ item.name }}
</li>
      </ul>
    </div>
    <div class="card-container">
      <!-- ALL 선택 시에만 버튼 보이게 설정 -->
      <button class="btn-prev" v-if="selectedMenu === 'ALL'" @click="prevPage">&lt;</button>
      
      <div 
        v-for="card in paginatedCards" 
        :key="card.id" 
        class="card"
      >
        <div class="card-image" 
             :style="{ backgroundImage: `url(${card.images})` }">
        </div>
        <p class="card_txt" v-html="card.name"></p>
      </div>

      <button class="btn-next" v-if="selectedMenu === 'ALL'" @click="nextPage">&gt;</button>
    </div>
  </div>
</template>

<script setup>
import { ref, computed, onMounted, onUnmounted } from 'vue';

const items = ref([
  { id: 1, name: "ALL" },
  { id: 2, name: "UI/UX Design" },
  { id: 3, name: "Animation" },
  { id: 4, name: "Java Script" }
]);

const cards = ref([
  { id: 1, name: "카드뉴스(포토샵)", category: "UI/UX Design", images: "./images/cardnews.png" },
  { id: 2, name: "카드뉴스(일러스트)", category: "UI/UX Design", images: "./images/newjeans.jpg" },
  { id: 3, name: "모바일 목업", category: "UI/UX Design", images: "./images/mockup.jpg" },
  { id: 4, name: "상세페이지(포토샵)", category: "UI/UX Design", images: "./images/detail.PNG" },
  { id: 5, name: "인터랙티브 웹 구현<br>Grid 레이아웃 적용", category: "Animation", images: "./images/grid.png" },
  { id: 6, name: "인터랙티브 웹 구현<br>스크롤 애니메이션", category: "Animation", images: "./images/scroll.png" },
  { id: 7, name: "Parallax 스크롤링", category: "Animation", images: "./images/parallax_scroll.png" },
  { id: 8, name: "프로그래스 바<br>애니메이션", category: "Animation", images: "./images/progressbar.png" },
  { id: 9, name: "비밀번호 입력 및<br>로그인 버튼 인터랙션", category: "Java Script", images: "./images/login.png" },
  { id: 10, name: "기념일 계산기", category: "Java Script", images: "./images/time_calc.png" },
  { id: 11, name: "Vue3에서 Chart.js 적용", category: "Java Script", images: "./images/chart.png" },
  { id: 12, name: "TO-DO LIST", category: "Java Script", images: "./images/todolist.png" }
]);

const selectedMenu = ref("ALL");
const currentPage = ref(0);
const itemsPerPage = 4;
//스크롤처리
const isVisible = ref(false);
const sectionThree = ref(null);

const handleScroll = () => {
  
  if (!sectionThree.value) return;

  const sectionTop = sectionThree.value.getBoundingClientRect().top;
  const windowHeight = window.innerHeight;

  if(sectionTop < windowHeight) {
    isVisible.value = true;
  } else {
    isVisible.value = false;
  }
}

onMounted(() => {
  window.addEventListener("scroll",handleScroll);
  handleScroll();
});

onUnmounted(() => {
  window.removeEventListener("scroll",handleScroll);
});

const selectedCategory = (category) => {
  selectedMenu.value = category; 
  currentPage.value = 0; 
};

const filteredCards = computed(() => {
  return selectedMenu.value === "ALL"
    ? cards.value
    : cards.value.filter(card => card.category === selectedMenu.value);
});

const totalPages = computed(() => {
  return Math.ceil(filteredCards.value.length / itemsPerPage);
});

const paginatedCards = computed(() => {
  const start = currentPage.value * itemsPerPage;
  const end = start + itemsPerPage;
  return filteredCards.value.slice(start, end);
});

const prevPage = () => {
  currentPage.value = currentPage.value === 0 ? totalPages.value - 1 : currentPage.value - 1;
};

const nextPage = () => {
  currentPage.value = (currentPage.value + 1) % totalPages.value;
};
</script>

<style scoped>
.section_three{
  display: flex;
  flex-direction: column;
  opacity: 0;
  transform: translateY(50px);
  transition: opacity 1.5s ease-out, transform 0.8s ease-out;
  margin-bottom: 200px;
}
.section_three.visible {
  opacity: 1;
  transform: translateY(0);
}
.section_three > h2{
  text-align: center;
  align-self: center;
  margin-bottom: 2rem;
}
.section_three .menu ul{
  display: flex;
  justify-content: center;
  gap: 2rem;
}
.menu li {
  cursor: pointer;
  padding: 5px 10px;
  position: relative;
  transition: transform 0.3s ease-in-out;
}

/* 기본 밑줄 효과 (hover 시) */
.menu li:not(.active)::after {
  content: "";
  display: block;
  width: 100%;
  height: 2px;
  background-color: #00bfff;
  position: absolute;
  bottom: -5px;
  left: 0;
  transform: scaleX(0);
  transition: transform 0.3s ease-in-out;
}

/* hover 시 밑줄 효과 적용 (단, .active에는 적용 안 됨) */
.menu li:not(.active):hover::after {
  transform: scaleX(1);
}

/* 선택된 항목 (active) 스타일 */
.active {
  border-bottom: 2px solid #00bfff;
  font-weight: bold;
}
/* 카드 리스트 스타일 */
.card-container {
  display: flex;
  flex-wrap: wrap;
  gap: 10px;
  margin-top: 20px;
  justify-content: center;
  position: relative;
}
/* 카드 버튼 */
button{
  background-color: transparent;
  border: none;
  font-size: 80px;
  position: absolute;
  cursor: pointer;
}
button:nth-of-type(1){
  top: 50%;
  left: 5%;
  transform: translateY(-50%);
}
button:nth-of-type(2){
  top: 50%;
  right: 5%;
  transform: translateY(-50%);
}
/* 카드 스타일 */
.card {
  width: 200px;
  height: 200px;
  background: #fff;
  border-radius: 10px;
  text-align: center;
  padding: 10px;
  margin: 20px;
}

/* 카드 이미지 */
.card-image {
  width: 100%;
  height: 100%;
  background-size: cover;
  background-position: center;
  border-radius: 8px;
}
.card_txt{
  font-size: 16px;
  padding: 20px;
  background-color: none; 
}
  /* 반응형 테블릿 */
  @media all and (max-width:1024px) { 
    /* 타이틀제목 */
    h2.section_title{
      max-width: 768px;
    }
    button:nth-of-type(1){
      top: 50%;
      left: 0%;
      transform: translateY(-50%);
    }
    button:nth-of-type(2){
      top: 50%;
      right: 0%;
      transform: translateY(-50%);
    }
    .card-container{
      display: flex;
      gap: 0;
    }
    .card{
      width: 160px;
      height: 160px;
    }
  }
  /* 반응형 모바일 max*/
  @media all and (max-width:768px) {
    h2.section_title{
      max-width: 400px;
      font-size: 50px;
    }
    .section_three .menu ul{
      width: 100%;
      gap: 0;
    }
    li.menu-item{
      font-size: 16px;
      white-space: nowrap;
    }
    .card{
      width: 140px;
      height: 140px;
      margin: 20px;
    }
    .card_txt{
      font-size: 12px;
      white-space: nowrap;
    }
    button{
      font-size: 50px;
    }


  }
/* 반응형 모바일 min */
  @media all and (max-width:479px) {
    .section_three{
      margin-bottom: 50px;
    }
    h2.section_title{
      max-width: 320px;
      font-size: 40px;
      text-align: center;
    }
    .card-container{
      gap: 0;
    }
    .card{
      width: 110px;
      height: 110px;
      margin: 20px;
    }
    .card > .card_txt{
      width: 100%;
      font-size: 12px;
      padding: 15px 0;
    }

    button{
      font-size: 50px;
    }button:nth-of-type(1){
      top: 50%;
      left: 0%;
      transform: translateY(-50%);
    }
    button:nth-of-type(2){
      top: 50%;
      right: 0%;
      transform: translateY(-50%);
    }
  }
</style>