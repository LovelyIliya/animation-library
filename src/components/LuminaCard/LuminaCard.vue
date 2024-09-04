<template>
  <div
    class="lumina-card"
    :style="{
      width: props.width + 'px',
      height: props.height + 'px',
      backgroundColor: props.backgroundColor,
      borderRadius: props.radius + 'px'
    }"
  >
    <div class="dazzle-light" ref="dazzleLight"></div>
  </div>
</template>

<script setup lang="ts">
import { ref, toRefs, onMounted } from 'vue'
const props = defineProps({
  width: {
    type: Number,
    default: 300
  },
  height: {
    type: Number,
    default: 200
  },
  backgroundColor: {
    type: String,
    default: 'rgba(255, 255, 255, 0.6)'
  },
  radius: {
    type: Number,
    default: 8
  },
  borderWidth: {
    type: Number,
    default: 3
  }
})
const { width, height, radius, borderWidth } = toRefs(props)
const dazzleLight = ref()
const path =
  `M${width.value - borderWidth.value - radius.value},${height.value} ` +
  `Q${width.value},${height.value},${width.value},${height.value - borderWidth.value - radius.value} ` +
  `L${width.value},${radius.value + 1} ` +
  `Q${width.value},0,${width.value - borderWidth.value - radius.value},0 ` +
  `L${width.value / 2},0 ` +
  `L${width.value / 2},${borderWidth.value} ` +
  `L${width.value - 2 - radius.value},${borderWidth.value} ` +
  `Q${width.value - borderWidth.value},${borderWidth.value},${width.value - borderWidth.value},14 ` +
  `L${width.value - borderWidth.value},${height.value - 2 - radius.value} ` +
  `Q${width.value - borderWidth.value},${height.value - borderWidth.value},${width.value - 2 - radius.value},${height.value - borderWidth.value} ` +
  `L14,${height.value - borderWidth.value} ` +
  `Q1,${height.value - borderWidth.value},${borderWidth.value},${height.value - 2 - radius.value} ` +
  `L${borderWidth.value},14 ` +
  `Q1,${borderWidth.value},14,${borderWidth.value} ` +
  `L${width.value / 2},${borderWidth.value} ` +
  `L${width.value / 2},0 ` +
  `L${radius.value + 1},0Q0,0,0,${radius.value + 1}L0,${height.value - borderWidth.value - radius.value} ` +
  `Q0,${height.value},${radius.value + 1},${height.value} ` +
  `L${width.value - borderWidth.value},${height.value} Z`

onMounted(() => {
  console.log(path)

  dazzleLight.value.style.clipPath = `path("${path}")`
})
</script>

<style lang="scss" scoped>
.lumina-card {
  backdrop-filter: blur(2px);
  position: relative;
}

.dazzle-light {
  width: 100%;
  height: 100%;
  clip-path: path('M0,0 Z');
  overflow: hidden;
  position: absolute;
  top: 0;
  left: 0;
  display: flex;
  align-items: center;
  justify-content: center;

  &::after {
    content: '';
    display: block;
    width: 60%;
    height: 200%;
    background: linear-gradient(90deg, transparent, red, transparent);
    animation: animation 5000ms infinite linear;
  }
}

@keyframes animation {
  0% {
    transform: rotateZ(0deg);
  }

  100% {
    transform: rotateZ(360deg);
  }
}
</style>
