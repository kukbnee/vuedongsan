<template>
  <!-- <Modal :oneroomsData="oneroomsData"
    :clickedDtlIdx="clickedDtlIdx"
    :handleModal="handleModal"
  /> -->
  <ModalVue 
    :popupYn="popupYn"
    :oneroomsData="oneroomsData"
    :clickedDtlIdx="clickedDtlIdx"
    v-on:closeModal="popupYn=false"
  />

  <div class="menu">
    <a>home</a>
    <a>shop</a>
    <a>about</a>
  </div>
  <DiscountVue />
  <CardVue v-for="(oneroom, idx) in oneroomsData" :key="idx"
    :oneroom="oneroom" :idx="idx"
    v-on:openModal="popupYn=true; clickedDtlIdx=$event;"
     
  />
  <!-- <div v-for="(oneroom, idx) in oneroomsData" :key="idx">
    <img :src="oneroom.image" class="room-img" />
    <h4 v-on:click="handleModal(idx)">{{oneroom.title}}</h4>
    <p>{{oneroom.price}}원</p>
  </div> -->
</template>

<script>

import oneroomsData from './assets/onerooms';
import DiscountVue from './DiscountVue.vue';
import ModalVue from './ModalVue.vue';
import CardVue from './CardVue.vue';

export default {
  name: 'App',
  data() {
    return {
      oneroomsData: oneroomsData,
      clickedDtlIdx: 0,
      popupYn: false
    }
  },
  methods : {
    increaseReportCnt(idx) {
      this.reportCnt[idx]++;
    },
    openModal() {
      
    },
    closeModal() {
      
    }
    // handleModal(idx) {
    //   this.popupYn = !this.popupYn;
    //   this.clickedDtlIdx = idx
    // }
  },
  components: {
    DiscountVue: DiscountVue,
    ModalVue: ModalVue,
    CardVue: CardVue
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
}
.menu {
  background: darkslateblue;
  padding: 15px;
  border-radius: 5px;
}
.menu a {
  color: white;
  padding: 15px;

}

.room-img {
  width: 100%;
  margin-top: 40px;
}

body {
  margin : 0;
}
div {
  box-sizing: border-box;
}
.black-bg {
  width: 100%; height:100%;
  background: rgba(0,0,0,0.5);
  position: fixed; padding: 20px;
}
.white-bg {
  width: 100%; background: white;
  border-radius: 8px;
  padding: 20px;
} 

</style>
