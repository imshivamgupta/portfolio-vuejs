<template>
  <div
    class="circle"
    ref="div"
    @mouseenter="hoverImage = true"
    @mouseleave="hoverImage = false"
  >
    <template v-if="threejs">
      <img v-show="!hoverImage" src="@/assets/3d.png" alt="" />
      <img
        v-show="hoverImage"
        src="@/assets/stand.png"
        alt=""
        class="hovered"
      />
    </template>
  </div>
</template>

<script>
import hoverEffect from 'hover-effect'
import image1 from '@/assets/normal.svg'
import image2 from '@/assets/hire.svg'
import Effect from '@/assets/dot.jpg'
export default {
  name: 'Circle-Gradient',
  props: ['threejs'],
  data() {
    return {
      hoverImage: false
    }
  },
  mounted() {
    if (this.threejs) {
      new hoverEffect({
        parent: this.$refs.div,
        intensity: 0.3,
        image1: image1,
        image2: image2,
        displacementImage: Effect
      })
    }
  }
}
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
  position: relative;
  img {
    position: absolute;
    right: 50%;
    bottom: 10%;
    width: 90%;
    height: 90%;
  }
  animation: slow-motion 4s ease-in-out infinite none alternate running;
  ::v-deep canvas {
    border-radius: 500px;
  }
}
</style>
