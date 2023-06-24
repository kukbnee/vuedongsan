<template>
  <!-- <Modal :oneroomsData="oneroomsData"
    :clickedDtlId="clickedDtlId"
    :handleModal="handleModal"
  /> -->
  <transition name="fade">
    <ModalVue 
      :popupYn="popupYn"
      :clickedObj="clickedObj"
      :clickedDtlId="clickedDtlId"
      v-on:closeModal="popupYn=false"
    />
  </transition>
  <div class="menu">
    <a>home</a>
    <a>shop</a>
    <a>about</a>
  </div>
  <DiscountVue />
  <button v-on:click="priceAscSort">가격낮은순</button>
  <button v-on:click="priceDscSort">가격높은순</button>
  <button v-on:click="titleSort">제목순</button>
  <CardVue v-for="(oneroom, idx) in oneroomsData" :key="idx"
    :oneroom="oneroom" :idx="idx"
    v-on:openModal="popupYn=true; clickedDtlId=$event.id; clickedObj=$event"
     
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
      clickedObj: {},
      clickedDtlId: 0,
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
      
    },
    priceAscSort() {
      this.oneroomsData.sort(function(a, b) {
        return a.price - b.price;
      });
    },
    priceDscSort() {
      this.oneroomsData.sort(function(a, b) {
        return b.price - a.price;
      });
    },
    titleSort() {
      this.oneroomsData.sort(function(a, b) {
        if(a.title < b.title) return -1;
        else if(a.title === b.title) return 0;
        else return 1;
      });
    }
    // handleModal(idx) {
    //   this.popupYn = !this.popupYn;
    //   this.clickedDtlId = idx
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
.fade-enter-from {
  /* 시작 */
  opacity: 0;
}
.fade-enter-active {
  transition: all 1s;
}
.fade-enter-to {
  /* 끝 */
  opacity: 1;
}
.fade-leave-from {
  /* 시작 */
  opacity: 1;
}
.fade-leave-active {
  transition: all 1s;
}
.fade-leave-to {
  /* 끝 */
  opacity: 0;
}

.start {
  opacity: 0;
  transition: all 1s;
}
.end {
  opacity: 1;
}
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
