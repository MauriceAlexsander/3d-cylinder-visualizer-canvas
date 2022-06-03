<template>
  <div class="canvas">
    <h3>Cylinder Visualizer</h3>
    <canvas ref="myCanvas" width="400" height="400"></canvas>
  </div>
</template>

<script lang="ts" setup>
import { defineProps, ref, Ref, watch } from "vue";

// Props
const props = defineProps({ 
  height: { type: Number, required: true },
  radius: { type: Number, required: true },
});

// Data
const myCanvas: Ref<HTMLCanvasElement | null> = ref(null);

watch(() => props.height, () => {
  draw();
});
watch(() => props.radius, () => {
  draw();
});


// Methods
const draw = () => {
  if (myCanvas.value == null) return;
  const ctx = myCanvas.value.getContext("2d")

  if (ctx == null) return;
  ctx.clearRect(0, 0, myCanvas.value.width, myCanvas.value.height)

  ctx.strokeStyle = '#f4f1de'
  ctx.lineWidth = 3

  const MAX_RADIUS = 200
  const MAX_HEIGHT = 400

  let height = props.height
  let radius = props.radius

  if (height >= radius * 2) {
    height = MAX_HEIGHT * 0.8
    radius = radius * height/props.height

    if ((radius + height) > MAX_HEIGHT && props.height <= MAX_HEIGHT) {
      height -= props.radius
      radius -= props.radius/2
    }
  }
  else {
    radius = MAX_RADIUS * 0.8
    height = height * radius/props.radius
  }

  ctx.beginPath();
  ctx.ellipse(MAX_RADIUS, (MAX_HEIGHT/2) - height/2, radius, radius/2, 0, 0, 2 * Math.PI);
  ctx.ellipse(MAX_RADIUS, (MAX_HEIGHT/2) + height/2, radius, radius/2, 0, 0, 2 * Math.PI);
  ctx.moveTo(MAX_RADIUS - radius, (MAX_HEIGHT/2) - height/2);
  ctx.lineTo(MAX_RADIUS - radius, (MAX_HEIGHT/2) + height/2);
  ctx.stroke();
}
</script>

<style lang="scss" scoped>
.canvas {
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
  width: 50%;
  color: #F2CC8F;
}

@media screen and (max-width: 1080px) and (max-height: 900px) {
  .canvas {
    display: none;
  }
}
</style>