<template>


  <!-- <div v-if="1==2">안녕하세요</div>
  <div v-else-if="1==3">안녕하세요2</div>
  <div v-else>안녕하세요3</div>
 -->
  <div>
    
    
    <Modal @closeModal="모달창열렸니=false;" :원룸들="원룸들" :누른거="누른거" :모달창열렸니="모달창열렸니" />
    
    <div class="menu">
      <a v-for="(menu) in menus" :key=menu.id>{{ menu.name }}</a>
      <a>Products</a>
      <a>About</a>
    </div>

    <Discount/>

    <Card @openModal="모달창열렸니=true; 누른거=$event" :a="원룸들[i]" v-for="(a , i) in 원룸들" :key=i></Card>

    

  </div>

</template>


<script>
import {data} from './assets/oneroom.js';
import Discount from './Discount.vue';
import Modal from './Modal.vue';
import Card from './Card.vue';


export default {
  name: 'App',
  data() {
    return {
      오브젝트 : {name : 'kim', age: 20},
      원룸들 : data,
      모달창열렸니: false,
      신고수: [0, 0, 0],
      menus: [{ id: 1, name: 'Home' }, { id: 2, name: 'Shop' }, { id: 3, name: 'About' }],
      price: [50, 60, 70],
      product: ['역삼동원룸', '천호동원룸', '마포구원룸'],
      images: [require('./assets/room0.jpg'), require('./assets/room1.jpg'), require('./assets/room2.jpg')],
      누른거:0,
    }
  },
  methods: {
    increase(index) {
      this.신고수[index] += 1
    },
    
  },
  components: {
    Discount,
    Modal,
    Card,
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




</style>
