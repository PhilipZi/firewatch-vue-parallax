<template>
  <div class="hero" :style="{ 'max-height': screenWidth }">
    <img
      src="../assets/background_parallax.png"
      class="parallax-layer layer1"
      :style="{ transform: `translateY(${scrollY * -0.7}px)` }"
    />
    <img
      src="../assets/layout_2.png"
      class="parallax-layer layer2"
      :style="{ transform: `translateY(${scrollY * -0.3}px)` }"
    />
    <img
      src="../assets/layer_1.png"
      class="parallax-layer layer3"
      :style="{ transform: `translateY(${scrollY * -0}px)` }"
    />
    <div class="reveal-layer"></div>
  </div>
  <div class="test"></div>
</template>

<script setup>
import { ref, onMounted, onBeforeUnmount } from "vue";

const scrollY = ref(0);
const screenWidth = ref(`${window.innerWidth * 0.6}px`);

const handleScroll = () => {
  scrollY.value = window.scrollY;
};

const handleResize = () => {
  screenWidth.value = `${window.innerWidth * 0.6}px`;
};

onMounted(() => {
  window.addEventListener("scroll", handleScroll);
  window.addEventListener("resize", handleResize);
  handleResize();
});

onBeforeUnmount(() => {
  window.removeEventListener("scroll", handleScroll);
});
</script>

<style scoped>
.hero {
  position: relative;
  height: 100vh;
  width: 100vw;
  overflow: hidden;
  background-color: #243541;
  display: block;
  z-index: 10;
  margin: 0;
}

.parallax-layer {
  position: absolute;
  z-index: 0;
  width: 100%;
}
.layer1 {
  z-index: 0;
}

.layer2 {
  z-index: 2;
  bottom: -50%;
}

.layer3 {
  z-index: 3;
  bottom: 0;
}

.test {
  width: 100%;
  height: 100vh;
  background-color: #243541;
}
</style>
