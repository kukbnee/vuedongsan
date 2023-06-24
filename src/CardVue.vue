<template>
  <div>
    <img :src="oneroom.image" class="room-img" />
    <h4 v-on:click="$emit('openModal', oneroom)">{{oneroom.title}}</h4>
    <p>{{oneroom.price}}원</p>
  </div>
</template>
,
<script>
export default {
  name: 'CardVue',
  props: {
    oneroom: Object,
    idx: Number
  }
}
</script>

<style>

</style>