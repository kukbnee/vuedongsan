<template>
  <div class="black-bg" v-if="popupYn === true">
    <div class="white-bg">
      <h4>{{clickedObj.title}}</h4>
      <img :src="clickedObj.image" class="room-img"/>
      <!-- <input v-on:input="month = $event.target.value" /> -->
      <input v-model.number="month" />
      <p> {{month}}개월 선택함: {{clickedObj.price * month}}원</p>
      <p>{{clickedObj.content}}</p>
      <button v-on:click="$emit('closeModal')">닫기</button>
    </div>
  </div>
</template>

<script>
export default {
  name: 'ModalVue',
  data() {
    return {
      month: 1
    }
  },
  watch: {
    month(a,b) {
      console.log(a,b);
      console.log(typeof a);
      // if(a >= 13) {
      //   this.month = 1;
      //   alert("개월수를 입력해주세요.");
      // }
      if(isNaN(this.month)) {
        alert("숫자만 입력해주세요.");
        this.month = 1;
      }
    }
  },
  props: {
    popupYn: Boolean,
    clickedObj: Object,
    clickedDtlIdx: Number,
  },
  beforeUpdate() {
    if(this.month < 3 && this.month !== '') {
      alert("3개월 이상 입력해야합니다.");
      this.month = 3;
    }
  }
}
</script>

<style>

</style>