<template>
  <div class="home">
    <Form v-model:height_model="height" v-model:radius_model="radius" />

    <CylinderCanvas :height="height" :radius="radius" />
  </div>
</template>

<script lang="ts" setup>
import {Ref, ref } from "vue";
import Form from "@/components/Form.vue";
import CylinderCanvas from "@/components/CylinderCanvas.vue";


const height: Ref<number> = ref(0);
const radius: Ref<number> = ref(0);
</script>

<style lang="scss" scoped>
.home {
  display: flex;
  justify-content: center;
  align-items: center;
  height: -webkit-fill-available;
}

@media screen and (max-width: 1080px) {
  .home {
    flex-direction: column-reverse;
    justify-content: flex-start;
    height: auto;
  }
}
</style>
