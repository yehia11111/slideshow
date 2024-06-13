<template>
  <div id="app">
    <div v-if="showVideo" class="video-container">
      <video @ended="onVideoEnd" autoplay muted>
        <source src="./assets/intro-video.mp4" type="video/mp4" />
        Your browser does not support the video tag.
      </video>
    </div>
    <div v-else class="slideshow">
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
      showVideo: true,
    };
  },
  mounted() {
    if (!this.showVideo) {
      this.startSlideshow();
    }
  },
  methods: {
    startSlideshow() {
      setInterval(() => {
        this.activeIndex = (this.activeIndex + 1) % this.images.length;
      }, 10000);
    },
    onVideoEnd() {
      this.showVideo = false;
      this.startSlideshow();
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
  opacity: 0.8;
}

.slideshow, .video-container {
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

.video-container video {
  width: 100%;
  height: 100%;
  object-fit: cover;
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

@media (min-width: 600px) {
  .logo {
    top: 30px;
    left: 50px;
  }

  .logo img {
    width: 300px;
  }

  .text {
    font-size: 44px;
    bottom: 10px;
    left: 10px;
  }
}

@media (min-width: 400px) and (max-width: 599.99px) {
  .logo {
    top: 20px;
    left: 20px;
  }

  .logo img {
    width: 150px;
  }

  .text {
    font-size: 20px;
    bottom: 8px;
    left: 8px;
  }
}

@media (min-width: 800px) and (max-width: 1199.99px) {
  .logo {
    top: 25px;
    left: 30px;
  }

  .logo img {
    width: 180px;
  }

  .text {
    font-size: 22px;
    bottom: 9px;
    left: 9px;
  }
}

@media (min-width: 1200px) and (max-width: 1599.99px) {
  .logo {
    top: 28px;
    left: 40px;
  }

  .logo img {
    width: 190px;
  }

  .text {
    font-size: 23px;
    bottom: 9px;
    left: 9px;
  }
}

@media (min-width: 1600px) and (max-width: 1919.99px) {
  .logo {
    top: 32px;
    left: 45px;
  }

  .logo img {
    width: 195px;
  }

  .text {
    font-size: 23.5px;
    bottom: 9.5px;
    left: 9.5px;
  }
}

@media (max-width: 399.99px) {
  .logo {
    top: 10px;
    left: 10px;
  }

  .logo img {
    width: 200px;
  }

  .text {
    font-size: 46px;
    bottom: 5px;
    left: 5px;
  }
}
</style>
