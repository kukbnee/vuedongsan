<template>
  <div class="discount" :style="display">
    <h4>지금 결재하면 {{discountRate}}% 할인</h4>
  </div>
</template>

<script>
export default {
  name: 'DiscountVue',
  data() {
    return {
      discountRate: 3,
      display: 'display: block'
    }
  },
  mounted() {
    let timer = setInterval(()=> {
      console.log(this.display,this.display.indexOf('none'));
      
      if(this.discountRate !== 0) {
        this.discountRate--;
      }else {
        this.display = 'display: none';
        clearInterval(timer);
      }
    }, 1000);
    
    
  }
}
</script>

<style>
.discount {
  background: #eee;
  padding: 10px;
  margin: 10px;
  border-radius: 5px;
}
</style>