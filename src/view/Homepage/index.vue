<template>
  <div class="homepage">
    <CircleGradient :style="circleVars" :threejs="threejs" />
    <CircleGradient :style="circleVarsSM1" />
    <CircleGradient :style="circleVarsSM2" />
    <div class="featured">
      <div class="emoji">✋</div>
      <div class="info">
        <span>Hello, I am</span>
        <h1>John Doe</h1>
      </div>
    </div>
    <div class="highlight first">
      <img
        :src="`${publicPath}assets/animation.jpg`"
        alt="animation"
        class="service-img service--animation"
      />
      <span>animation</span>
    </div>
    <div class="highlight second">
      <img
        :src="`${publicPath}assets/interaction.jpg`"
        alt="interaction"
        class="service-img service--interaction"
      />
      <span>interaction</span>
    </div>
    <div class="highlight third">
      <img
        :src="`${publicPath}assets/illustration.png`"
        alt="illustration"
        class="service-img service--illustration"
      />
      <span>illustration</span>
    </div>
    <img src="@/assets/abstract/rotated-dots.svg" alt="" class="rotated-dots" />
    <img src="@/assets/abstract/cross.svg" alt="" class="cross" />
    <img src="@/assets/abstract/cross.svg" alt="" class="cross c2" />
    <img src="@/assets/abstract/wavy.svg" alt="" class="wavy" />
    <img src="@/assets/abstract/wavy.svg" alt="" class="wavy w2" />
    <img src="@/assets/abstract/dots.svg" alt="" class="dots" />
  </div>
</template>

<script>
import CircleGradient from '@/components/Utilities/CircleGradient'
import { gsap, Power3 } from 'gsap'
export default {
  name: 'Home',
  components: {
    CircleGradient
  },
  computed: {
    circleVars() {
      return {
        '--width': '500px'
      }
    },
    circleVarsSM1() {
      return {
        '--width': '80px'
      }
    },
    circleVarsSM2() {
      return {
        '--width': '150px'
      }
    }
  },
  data() {
    return {
      publicPath: process.env.BASE_URL,
      threejs: true
    }
  },
  created() {
    window.addEventListener('load', this.onWindowLoad)
  },
  methods: {
    onWindowLoad() {
      this.$emit('loaded')
      this.imageAnim()
    },
    imageAnim() {
      gsap.from('.highlight,.circle', {
        alpha: 0,
        duration: 1,
        delay: 1,
        stagger: 0.1,
        ease: Power3.easeInOut
      })
    }
  },
  mounted() {}
}
</script>

<style lang="scss" scoped>
.homepage {
  position: relative;
  padding: 1.5rem;
  height: calc(100vh - 78px);
  .circle {
    position: absolute;
    left: calc(50% - (var(--width)) / 2);

    &:nth-child(2) {
      top: 60%;
      left: 10%;
    }

    &:nth-child(3) {
      top: 90%;
      left: 25%;
    }
  }

  .featured {
    padding: 1.5rem;
    border-radius: 15px;
    background: #edf2f8;
    box-shadow: 30px 30px 60px #c9ced3, -30px -30px 60px #ffffff;
    @include flex-center;
    display: inline-flex;
    .emoji {
      font-size: 3rem;
      margin-right: 1rem;
      transform: rotate(-35deg);
      transform-origin: bottom;
      animation: slow-motion-hi 1s ease-in-out infinite none alternate running;
    }
  }

  // Right side Bubbles
  .highlight {
    position: absolute;
    @include flex-center();
    flex-direction: column;
    span {
      margin-top: 0.6rem;
      font-size: 14px;
      color: rgba($color: #000000, $alpha: 0.5);
    }
    &.first {
      top: 0;
      right: 250px;
    }
    &.second {
      right: 0;
      top: 40%;
      transform: translateY(-50%);
    }
    &.third {
      bottom: 10%;
      right: 200px;
    }
    .service-img {
      border-radius: 500px;
      object-fit: cover;
      box-shadow: 15px 15px 30px #c9ced3a6, -15px -15px 30px #ffffff;
      &.service--animation {
        width: 120px;
        height: 120px;
      }
      &.service--interaction {
        width: 250px;
        height: 250px;
      }
      &.service--illustration {
        width: 150px;
        height: 150px;
      }
    }
  }

  .rotated-dots {
    position: absolute;
    top: 0;
    z-index: -1;
    left: 150px;
  }
  .dots {
    position: absolute;
    right: 0;
    top: 0;
    z-index: -1;
  }
  .wavy {
    position: absolute;
    z-index: -1;
    right: 350px;
    &.w2 {
      bottom: 50px;
      left: 150px;
    }
  }
  .cross {
    position: absolute;
    z-index: -1;
    left: 500px;
    opacity: 0.4;
    &.c2 {
      bottom: 50px;
      left: 120px;
    }
  }
}
</style>
