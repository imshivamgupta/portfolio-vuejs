<template>
  <div class="circle"></div>
</template>

<script>
export default {
  name: "Circle-Gradient",
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
}
</style>