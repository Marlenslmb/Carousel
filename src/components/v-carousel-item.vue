<template>
  <div class="v-carousel-item">
    <div class="mainImages_block">
      <img class="mainImages" :src=" require('../assets/images/' + item_data.img) " v-if="imageSlide" >
      <div class="item_content" v-else>
        <p>{{item_data.name}}</p>
        <p>{{item_data.id}}</p>
      </div>
    </div>
    <div class="textBlock">
      <h3 class="imageTittle">{{item_data.title}}</h3>
    </div>
    <div class="iconsBlock">
      <img @click="redirectFacebook" class="iconImages" src="https://img.icons8.com/material-outlined/24/000000/facebook-new.png"/>
      <img @click="redirectTwitter" class="iconImages" src="https://img.icons8.com/fluency/48/000000/twitter.png"/>
      <img @click="redirectInstagram" class="iconImages" src="https://img.icons8.com/material-outlined/24/000000/instagram-new--v1.png"/>
    </div>
  </div>
</template>

<script>
export default {
  name: "v-carousel-item",
  props: {
    item_data: {
      type: Object,
      default: () => {}
    },
    imageSlide: {
      type: Boolean,
      default: true
    }
  },
  methods: {
    redirectFacebook() {
      window.location = 'https://www.facebook.com/'
    },
    redirectTwitter() {
      window.location = 'https://twitter.com/?lang=ru'
    },
    redirectInstagram() {
      window.location = 'https://www.instagram.com/'
    },
  }
}
</script>

<style>
.v-carousel-item{
  border-radius: 10px;
  border: 1px solid black;
  padding: 15px;
  margin-right: 10px;
}
.mainImages{
  max-height: 250px;
  border-radius: 10px;
}
.imageTittle{
  margin-bottom: 0;
}
.iconsBlock{
  display: flex;
  justify-content: center;
  height: 100px;
  align-items: center;
}
.iconImages{
  width: 35px;
  height: 35px;
}
</style>