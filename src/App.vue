<template>
  <div>
    <!-- <div class="start" :class="{end : 모달창열렸니}"> -->
    <transition name="fade">
      <Modal  @closeModal= "모달창열렸니=false" :원룸들 = '원룸들' :누른거 = '누른거' :모달창열렸니 = '모달창열렸니'/>
    <!-- </div> -->
  </transition>
    <div class="menu">
      <a v-for="menu in menus" :key="menu">{{ menu }}</a>
    </div>
<Discount/>

<button @click="priceSort">가격순정렬</button>
<button @click="sortBack">되돌리기</button>

    <!-- <img alt="Vue logo" src="./assets/logo.png" />\ -->
<Card @openModal= "모달창열렸니=true; 누른거=$event"  :원룸들 = '원룸들[i]' v-for="(원룸,i) in 원룸들" :key="i"/>
    
  </div>
</template>

<script>
import data from "./data.js";
import Discount from "./Discount.vue";
import Modal from "./Modal.vue";
import Card from "./Card.vue";

export default {
  name: "App",
  data() {
    return {
      
      
      원룸들오리지널 : [...data],
      누른거 : 0,
      원룸들: data,
      모달창열렸니: false,
      신고수: [0, 0, 0],
      products: ["역삼동원룸", "천호동원룸", "마포구원룸"],
      menus: ["Home", "Products", "About"],
    };
  },

  methods: {
    increase(q) {
      this.신고수[q]++;
    },
    sortBack(){
      this.원룸들 = [...this.원룸들오리지널];
    },
    priceSort(){
      this.원룸들.sort((a, b) =>{
        return a.price - b.price
      })
    }
  },

   mounted(){
  //   setTimeout(()=>{this.showDiscount=false},2000)

  // setInterval(() => {
  //       return this.amount--;
        
  //     }, 1000);
   },
  components: {
    Discount : Discount,
    Modal : Modal,
    Card : Card,
  },
};
</script>

<style>
.fade-leave-from{
  opacity: 1;
}
.fade-leave-active{
  transition: all 1s;
}
.fade-leave-to{
  opacity: 0;
}
.fade-enter-from{
  transform: translateY(-1000px);
  /* opacity: 0; */
}
.fade-enter-active{
  transition: all 1s;
}
.fade-enter-to{
  transform: translateY(0px);
  /* opacity: 1; */
}
.start{
  opacity: 0;
  transition: all 1s;
}
.end{
  opacity: 1;
}

body {
  margin: 0;
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
.room-img {
  width: 100%;
  margin-top: 40px;
}
</style>
