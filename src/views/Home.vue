<template>
  <div class="home">
    <Form msg="Welcome to Your Vue.js + TypeScript App" />

    <CilinderCanvas />
  </div>
</template>

<script lang="ts" setup>
import Form from "@/components/Form.vue";
import CilinderCanvas from "@/components/CilinderCanvas.vue";
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
  }
}
</style>
