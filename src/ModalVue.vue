<template>
  <div class="black-bg" v-if="popupYn === true">
    <div class="white-bg">
      <h4>{{oneroomsData[clickedDtlIdx].title}}</h4>
      <img :src="oneroomsData[clickedDtlIdx].image" class="room-img"/>
      <p>가격: {{oneroomsData[clickedDtlIdx].price}}원</p>
      <p>{{oneroomsData[clickedDtlIdx].content}}</p>
      <button v-on:click="$emit('closeModal')">닫기</button>
    </div>
  </div>
</template>

<script>
export default {
  name: 'ModalVue',
  props: {
    popupYn: Boolean,
    oneroomsData: Array,
    clickedDtlIdx: Number,
  }
}
</script>

<style>

</style>