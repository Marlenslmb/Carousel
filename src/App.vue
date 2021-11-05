<template>
  <div id="app">
    <v-carousel
      :carousel_data="sliderItems"
    >
<!--      :interval="2000"-->

    </v-carousel>
  </div>
</template>

<script>
import vCarousel from './components/v-carousel'
export default {

  name: 'App',
  components: {
    vCarousel
  },
  data() {
    return {
      sliderItems: [
        {id: 1, title: 'Cars', name: 'img1', img: '1.jpg'},
        {id: 2, title: 'BMW', name: 'img2', img: '2.jpg'},
        {id: 3, title: 'Mercedes-Benz ZZZ', name: 'img3', img: '3.jpg'},
        {id: 4, title: 'Audi A8', name: 'img4', img: '4.jpg'},
        {id: 5, title: 'Motorbike', name: 'img5', img: '5.jpg'},
        {id: 6, title: 'Lambo', name: 'img6', img: '6.jpg'},
      ]
    }
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
  margin-top: 60px;
}
</style>
