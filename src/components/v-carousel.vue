<template>
  <div class="wrapper">
    <div class="v-carousel">
<!--      :style="{'margin-left': '-' + (100 * currentSlideIndex) + '%'}"-->
      <v-carousel-item
          v-for="item in activeItems"
          :key="item.id"
          :item_data="item"
      >
      </v-carousel-item>
    </div>
    <div class="btnBlock">
      <button @click="prevSlide"><i class="arrow left"></i></button>
      <button @click="nextSlide"><i class="arrow right"></i> </button>
    </div>
  </div>
</template>

<script>
import vCarouselItem from './v-carousel-item'
export default {
  name: "v-carousel",
  components: {
    vCarouselItem
  },
  props: {
    carousel_data: {
      type: Array,
      default: () => []
    },
    interval: {
      type: Number,
      default: 0
    },
  },
  data() {
    const limit = 3;
    let limitArray = [];
    for(let i = 0; i < limit; i++) {
      limitArray.push(i)
    }
    return{
      currentSlideIndex: 0,
      limitArray,
    }
  },
  computed: {
    activeItems() {
      return [...this.limitArray].map((item) => {
        return this.carousel_data[item]
      })
    }
  },
  methods: {
    prevSlide(){
      if(this.currentSlideIndex > 0){
        this.currentSlideIndex --
      }
      this.limitArray = [...this.limitArray].map(item => {
        return item -1
      })
    },
    nextSlide() {
      if(this.currentSlideIndex >= this.carousel_data.length -1) {
        this.currentSlideIndex = 0
      }else{
        this.currentSlideIndex ++
      }
      this.limitArray = [...this.limitArray].map(item => {
        return item +1
      })
    }
  },
  mounted() {
    if(this.interval > 0){
      let vm = this;
      setInterval( () => {
        vm.nextSlide()
      }, vm.interval)
    }
  }
}
</script>

<style scoped>
  .wrapper{
    overflow: hidden;
    margin: 0 auto;
    max-width: 100%;
    position: relative;
    display: flex;
  }
  .v-carousel{
    display: flex;
    transition: all ease .5s;
    width: 90%;
    margin: 0 auto !important;
    justify-content: space-evenly;

  }
  .btnBlock{
    display: flex;
    align-items: center;
    position: absolute;
    justify-content: space-between;
    height: 100%;
    width: 100%;
  }
  button{
    margin-top: 10px;
    /*width: 80px;*/
    /*height: 40px;*/
    background: none;
    border-radius: 8px;
    color: black;
    border: none;

  }
  i {
    border: solid black;
    border-width: 0 3px 3px 0;
    display: inline-block;
    padding: 3px;
  }
  .right {
    transform: rotate(-45deg);
    -webkit-transform: rotate(-45deg);
    height: 25px;
    width: 25px;
  }
  .left {
    transform: rotate(135deg);
    -webkit-transform: rotate(135deg);
    height: 25px;
    width: 25px;
  }
</style>