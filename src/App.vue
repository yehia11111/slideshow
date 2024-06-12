<template>
  <div id="app">
    <div class="slideshow">
      <div
        v-for="(image, index) in images"
        :key="index"
        :class="['slide', { active: index === activeIndex }]"
        :style="{ backgroundImage: `url(${image})` }"
      ></div>
    </div>
    <div class="logo">
      <img src="./assets/logo.jpeg" alt="Logo">
    </div>
    <p class="text">Mersvo</p>
  </div>
</template>

<script>
import img1 from './assets/gettyimages-1850831883-612x612.jpg';
import img2 from './assets/gettyimages-1369535498-612x612.jpg';
import img3 from './assets/gettyimages-1246896014-1024x1024.jpg';

export default {
  name: 'App',
  data() {
    return {
      images: [img1, img2, img3],
      activeIndex: 0,
    };
  },
  mounted() {
    this.startSlideshow();
  },
  methods: {
    startSlideshow() {
      setInterval(() => {
        this.activeIndex = (this.activeIndex + 1) % this.images.length;
      }, 10000);
    },
  },
};
</script>

<style>
#app {
  position: relative;
  height: 100vh;
  width: 100vw;
  overflow: hidden;
}

.logo {
  position: absolute;
  top: 30px;
  left: 50px;
  z-index: 10;
}

.logo img {
  width: 200px;
  height: auto;
  opacity: 0.8; /* Make the logo slightly transparent */
}

.slideshow {
  width: 100%;
  height: 100%;
  position: absolute;
  top: 0;
  left: 0;
}

.slide {
  width: 100%;
  height: 100%;
  background-size: contain;
  background-position: center;
  background-repeat: no-repeat;
  opacity: 0;
  transition: opacity 1s ease-in-out;
  position: absolute;
}

.slide.active {
  opacity: 1;
}

.text {
  position: absolute;
  bottom: 10px;
  left: 10px;
  color: black;
  font-size: 24px;
  z-index: 10;
  background: rgba(255, 255, 255, 0.5);
  padding: 5px;
}
</style>
