<template>
  <div class="canvas">
    <h3>Cylinder Visualizer</h3>
    <canvas id="canvas" width="400" height="400"></canvas>
  </div>
</template>

<script lang="ts" setup>
import { defineProps, onMounted, watch } from "vue";
import * as THREE from 'three';
import { OrbitControls } from 'three/examples/jsm/controls/OrbitControls';

// Props
const props = defineProps({ 
  height: { type: Number, required: true },
  radius: { type: Number, required: true },
});

const scene = new THREE.Scene();
scene.background = new THREE.Color('#3d405b')

const camera = new THREE.PerspectiveCamera(75, 1, 0.1, 1000);
camera.position.setY(15);
camera.position.setZ(20);

let renderer: THREE.WebGLRenderer;
let controls: any;

const geometry = new THREE.CylinderGeometry(10, 10, 20, 16, 1);
const material = new THREE.MeshStandardMaterial( {color: '#e07a5f'});
const cylinder = new THREE.Mesh(geometry,  material);
scene.add(cylinder);

const pointLight = new THREE.PointLight('#fff', 5, 100);
pointLight.position.set(50, 50, 50);

const ambientLight = new THREE.AmbientLight('#fff')
scene.add(ambientLight, pointLight);

function animate() {
  requestAnimationFrame(animate);

  controls.update();

  renderer.render(scene, camera);
}

const updateCylinder = () => {
  let scaleFactorX = props.radius / cylinder.geometry.parameters.radiusTop;
  let scaleFactorZ = props.radius / cylinder.geometry.parameters.radiusBottom;
  let scaleFactorY = props.height / cylinder.geometry.parameters.height;
  cylinder.scale.set(scaleFactorX, scaleFactorY, scaleFactorZ);
}

onMounted(() => {
  renderer = new THREE.WebGLRenderer({canvas: document.querySelector('#canvas') as HTMLCanvasElement})
  renderer.setPixelRatio(1);
  renderer.setSize(300, 300);
  renderer.render(scene, camera);

  controls = new OrbitControls(camera, renderer.domElement)
  animate()
})

watch(() => props.height, () => {updateCylinder()});
watch(() => props.radius, () => {updateCylinder()});

</script>

<style lang="scss" scoped>
.canvas {
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
  width: 50%;
  color: var(--yellow);
}

@media screen and (max-width: 1080px) and (max-height: 900px) {
  .canvas {
    width: 100%;
  }
}
</style>