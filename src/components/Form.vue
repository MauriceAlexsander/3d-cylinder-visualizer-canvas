<template>
  <div class="form">
    <input type="text" class="form-control">
    <input type="text" class="form-control">
    {{props.msg}}
    <button type="submit" class="btn">Calcular</button>
  </div>
</template>

<script lang="ts" setup>
import { defineProps } from "vue";

const props = defineProps({msg: String})
</script>

<style scoped lang="scss">
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
