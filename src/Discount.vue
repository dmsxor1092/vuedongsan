<template>
  <div class="discount" v-if="showDiscount == true">
  <h4>지금 결제하면 {{amount}}% 할인</h4>
</div>
</template>

<script>
export default {
    //eslint-disable-next-line
    name: 'Discount',
    data() {
      return{
        amount : 30,
        showDiscount : true,
        start : null,
      }
    },

    mounted(){
      this.start = setInterval(() => {
                  
                   if(this.amount != 0) {
                    return this.amount--;
                    
                   }else{
                    clearInterval(this.start);
                    this.showDiscount = false;
                   }
                  }, 1000);
    }

}
</script>

<style>
.discount{
  background: #eee;
  padding: 10px;
  margin: 10px;
  border-radius: 5px;
}
</style>