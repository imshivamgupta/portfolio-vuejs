<template>
  <div class="circle" ref="div">
    <template v-if="threejs"> </template>
  </div>
</template>

<script>
import hoverEffect from "hover-effect";
import image1 from "@/assets/logo.png";
import image2 from "@/assets/logo.png";
import Effect from "@/assets/heightMap.png";
export default {
  name: "Circle-Gradient",
  props: ["threejs"],
  mounted() {
    if (this.threejs) {
      new hoverEffect({
        parent: this.$refs.div,
        intensity: 0.3,
        image1: image1,
        image2: image2,
        displacementImage: Effect,
      });
    }
  },
};
</script>

<style lang="scss" scoped>
.circle {
  $width: var(--width);
  width: $width;
  height: $width;
  background: linear-gradient(
    115deg,
    rgba(254, 254, 254, 0.2) 7%,
    rgba(217, 225, 234, 1) 100%
  );
  border-radius: 50%;
  animation: slow-motion 4s ease-in-out infinite none alternate running;
  ::v-deep canvas {
    border-radius: 500px;
  }
}
</style>