<template>
  <div class="homepage">
    <CircleGradient :style="circleVars" />
    <CircleGradient :style="circleVarsSM1" />
    <CircleGradient :style="circleVarsSM2" />
    <div class="featured">
      <div class="emoji">✋</div>
      <div class="info">
        <span>Hello, I am</span>
        <h1>Shivam</h1>
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
    <div class="my-div" style="width: 300px; height: 300px" ref="div"></div>
  </div>
</template>

<script>
import CircleGradient from "@/components/Utilities/CircleGradient";
import hoverEffect from "hover-effect";
import image1 from "@/assets/img1.png";
import image2 from "@/assets/img2.png";
import Effect from "@/assets/heightMap.png";
export default {
  name: "Home",
  components: {
    CircleGradient,
  },
  computed: {
    circleVars() {
      return {
        "--width": "500px",
      };
    },
    circleVarsSM1() {
      return {
        "--width": "80px",
      };
    },
    circleVarsSM2() {
      return {
        "--width": "150px",
      };
    },
  },
  data() {
    return {
      publicPath: process.env.BASE_URL,
    };
  },
  mounted() {
    new hoverEffect({
      parent: this.$refs.div,
      intensity: 0.3,
      image1: image1,
      image2: image2,
      displacementImage: Effect,
    });
  },
};
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
      top: 50%;
      transform: translateY(-50%);
    }
    &.third {
      bottom: 10%;
      right: 280px;
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
  .my-div {
    border-radius: 500px;
    position: absolute;
    bottom: 0;
    left: 30%;
    display: none;
  }
}
</style>