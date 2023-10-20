<script setup>
import posts from "./datas/post";
</script>

<template>
  <div class="black-bg" v-if="modal === true">
    <div class="white-bg">
      <h3>상세페이지</h3>
      <h4>상세페이지 내용 ! ! !</h4>
      <button @click="modal = false">닫기</button>
    </div>
  </div>

  <!--Vue에서 동적UI 만들때 :
    1. UI 디자인 만들어 두기
    2. UI의 현재상태를 데이터로 만들기 ex) 모달이 현재 열려있는지 아닌지 등등
    3. 데이터에 따라 UI가 어떻게 보일지 작성 ex) v-if="조건문"
  -->

  <div class="menu">
    <a v-for="x in menuName" :key="x">{{ x }}</a>
  </div>

  <!--Vue 반복문
1. <태그 v-for=" name in 반복횟수" :key="name">
2. <태그 v-for=" name in array/object" :key="name">
-->

  <!-- <div class="product" v-for="(a, i) in products" :key="i">
    <h4>{{ a }}</h4>
    <h4>{{ price[i] }}</h4>
  </div> -->

  <div v-for="(a, i) in posts" :key="i">
    <img :src="posts[i].image" class="image-size" />
    <h3>{{ a.title }}</h3>
    <h4>{{ a.content }}</h4>
    <h4>{{ a.price }}원</h4>
  </div>
  <!-- <div class="product">
    <img :src="posts[0].image" class="image-size" />
    <h3 @click="modal = true">{{ posts[0].title }}</h3>
    <h4>{{ posts[0].price }}원</h4>
    <h4>{{ posts[0].content }}</h4>
    <button @click="신고수[0]++">허위매물 신고</button>
    <span>신고수 : {{ 신고수[0] }}</span>
  </div>

  <div class="product">
    <img src="./assets/img1.jpeg" class="image-size" />
    <h3>{{ products[1] }}</h3>
    <h4>70만원</h4>
    <button @click="신고수[1]++">허위매물 신고</button>
    <span>신고수 : {{ 신고수[1] }}</span>
  </div>

  <div class="product">
    <img src="./assets/img1.jpeg" class="image-size" />
    <h3>{{ products[2] }}</h3>
    <h4>100만원</h4>
    <button @click="신고수[2]++">허위매물 신고</button>
    <span>신고수 : {{ 신고수[2] }}</span>
  </div> -->

  <!--Vue 이벤트 핸들러 :
  v-on:click="" / @click=""
-->

  <!--Vue에서 데이터 바인딩 하는법 :
1. script 태그 내에 data(){return{}} 데이터저장소 를 만들어 두고 object자료 형식으로 작성 후 {{데이터이름}}
2. HTML태그 속성도 데이터바인딩가능 -> 속성앞에 : 붙여주면 됨 ex) :속성="데이터이름"
--></template>

<script>
export default {
  name: "App",
  data() {
    return {
      modal: false,
      신고수: [0, 0, 0],
      menuName: ["HOME", "SHOP", "CONTACT"],
      products: posts,
      // price: ["50만원", "70만원", "100만원"],
    };
  },
  methods: {},
  components: {},
};
</script>

<!--Vue 에서 함수 만들때 :
1. methods:{ 함수명(){} }
2. 함수안에서 데이터 사용할때 this.데이터명 -->

<style scoped>
body {
  margin: 0;
}

div {
  box-sizing: border-box;
}

.black-bg {
  width: 100%;
  height: 100%;
  background-color: rgb(0, 0, 0, 0.5);
  position: fixed;
  padding: 20px;
}
.white-bg {
  width: 100%;
  background-color: white;
  border-radius: 8px;
  padding: 20px;
}

.image-size {
  width: 100%;
  height: 30%;
}
.product {
  margin: 20px;
}

.menu {
  background-color: lightgray;
  padding: 10px;
  margin-bottom: 30px;
  border-radius: 5px;
  text-align: center;
}

.menu a {
  font-weight: bold;
  color: black;
  padding: 20px;
}

button {
  margin-right: 10px;
  background-color: red;
  color: white;
  border: none;
  border-radius: 5px;
  font-weight: bold;
}
</style>
