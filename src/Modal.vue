<template>
  <div class="black-bg" v-if="모달창열렸니">
      <div class="white-bg">
        <img :src="원룸들[누른거].image">
        <h4>{{원룸들[누른거].title}}</h4>
        <p>{{ 원룸들[누른거].content }}</p>
        
        <input v-model.number="month"> <!-- 약어 -->

        <p> {{ month }} 개월 선택함 : {{ 원룸들[누른거].price * month }} </p>
        <p>{{ 원룸들[누른거].price }} 원</p>

        <!-- <input type="checkbox" v-model.number="month"> -->

        <!-- <select v-model="month">
            <option>1</option>
            <option>2</option>
            <option>3</option>
        </select> -->
        <p>{{ selectValue }}</p>
        <button @click="$emit('closeModal')">닫기</button>
        <!-- <button @click="log()">확인</button> -->
        
      </div>
    </div>
</template>

<script>
export default {
    name : 'ModalComponent',
    data(){
        return{
            month : 1,
        }
    },
    watch : {
        month(a){
      if (isNaN(a) == true){
        alert('문자입력하지마라');
        this.month = 1;
      }else if(a>12){
        alert('13이상 적지마라');
        this.month = 12;
      }
    },
    },
    props :{
        원룸들 : Object, /* 데이터 형식을 적는다 Stirng, Array*/
        누른거 : Number,
        모달창열렸니 : Boolean,
    },
    methods :{
        log(){
            console.log(this.month)
            
        }
    }
}
</script>

<style>
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