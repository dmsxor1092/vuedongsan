<template>
   <div class="black-bg" v-if="모달창열렸니==true" >
      <div class="white-bg">
        <img :src="원룸들[누른거].image" class="room-img" />
        <h4>{{원룸들[누른거].title}}</h4>
        <p>{{원룸들[누른거].content}}</p>
        <input v-model="month">
        <p>{{month}}개월 선택함 : {{원룸들[누른거].price*month}} 원</p>
       
        <button @click="$emit('closeModal')">닫기</button>
      </div>
    </div>
</template>

<script>

export default {
    //eslint-disable-next-line
name:"Modal",
data(){
      return{
        month : 1,
      }
    },
    watch :{
      month(a){
        //var pattern = /\s/g;
        if(isNaN(a)==true){
          alert('문자 입력 하지마라')
          this.month = 1;
        // }else if(a.match(pattern)){
        //   alert('스페이스바 치치마')
        // }
        }
      }
    },

props:{
   
    원룸들 : Object,
    누른거 : Number,
    모달창열렸니 : Boolean,
}
}
</script>

<style>

</style>