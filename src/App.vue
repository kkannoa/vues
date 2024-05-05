<template>
  <div>
    <div class="black-bg" v-if="모달창열렸니">
      <div class="white-bg">
        <h4>상세페이지임</h4>
        <p>상세페이지 내용임</p>
        <button @click="모달창열렸니 = false">닫기</button>
      </div>
    </div>

    <div class="menu">
      <a v-for="(menu) in menus" :key=menu.id>{{ menu.name }}</a>
      <a>Products</a>
      <a>About</a>
    </div>

    <div>
      원룸샾
    </div>

    <div v-for="(product, i) in product" :key="i" >
      <div @click="모달창열렸니 = true">
      <img :src="images[i]">
      <!-- <img src="./assets/room0.jpg" alt="Product image"> -->
      <h4>{{ product }}</h4>
    </div>
      <p>{{ price[i] }} 만원</p>
      <button @click="increase(i)">허위매물신고</button>
      <span>신고수 : {{ 신고수[i] }} </span>

    </div>
  </div>
</template>

<script>



export default {
  name: 'App',
  data() {
    return {
      모달창열렸니: false,
      신고수: [0, 0, 0],
      menus: [{ id: 1, name: 'Home' }, { id: 2, name: 'Shop' }, { id: 3, name: 'About' }],
      price: [50, 60, 70],
      product: ['역삼동원룸', '천호동원룸', '마포구원룸'],
      images: [require('./assets/room0.jpg'), require('./assets/room1.jpg'), require('./assets/room2.jpg')],
    }
  },
  methods: {
    increase(index) {
      this.신고수[index] += 1
    },
  },
  components: {
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

.menu {
  background: darkslateblue;
  padding: 15px;
  border-radius: 5px;
}

.menu a {
  color: white;
  padding: 10px;
}

body {
  margin: 0
}

div {
  box-sizing: border-box;
}

.black-bg {
  width: 100%;
  height: 100%;
  background: rgba(0, 0, 0, 0.5);
  position: fixed;
  padding: 20px;

}

.white-bg {
  width: 100%;
  background: white;
  border-radius: 8px;
  padding: 20px;

}
</style>
