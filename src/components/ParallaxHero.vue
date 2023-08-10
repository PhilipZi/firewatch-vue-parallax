<template>
  <div class="hero" :style="{ 'max-height': screenWidth }">
    <img
      src="../assets/background_parallax.png"
      class="parallax-layer layer1"
      :style="{ transform: `translateY(${scrollY * -0.2}px)` }"
    />
    <img
      src="../assets/layout_2.png"
      class="parallax-layer layer2"
      :style="{ transform: `translateY(${scrollY * -0.6}px)` }"
    />
    <img
      src="../assets/layer_1.png"
      class="parallax-layer layer3"
      :style="{ transform: `translateY(${scrollY * -0}px)`, width: `100%` }"
    />
    <div class="reveal-layer"></div>
  </div>
  <div class="test"></div>
</template>

<script>
export default {
  data() {
    return {
      scrollY: 0,
      screenWidth: `${window.innerWidth * 0.6}px`,
    };
  },
  mounted() {
    window.addEventListener("scroll", this.handleScroll);
    window.addEventListener("resize", this.handleResize); // Event für Fenstergrößenänderungen hinzufügen

    this.handleResize();
  },

  beforeDestroy() {
    window.removeEventListener("scroll", this.handleScroll);
  },
  methods: {
    handleScroll() {
      this.scrollY = window.scrollY;
    },
    handleResize() {
      this.screenWidth = `${window.innerWidth * 0.6}px`; // Bildschirmbreite aktualisieren
    },
  },
};
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
}

.layer1 {
  position: absolute;
  z-index: 0;
  width: 100%;
}

.layer2 {
  position: absolute;
  z-index: 2;
  bottom: -50%;
  width: 100%;
}

.layer3 {
  position: absolute;
  z-index: 3;
  bottom: 0;
}

.test {
  width: 100%;
  height: 100vh;
  background-color: #243541;
  position: relative;
  z-index: 98;
  margin: 0;
  padding: 0;
  border: 0;
  vertical-align: top;
}
</style>
