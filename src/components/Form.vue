<template>
  <div class="form-container">
    <form>
      <label for="height">height (meters)</label>
      <input v-model="height" name="height" type="number" class="form-control" min="0" step="any">

      <label for="radius">radius (meters)</label>
      <input v-model="radius" name="radius" type="number" class="form-control" min="0" step="any">

      <p>Volume: {{volume}}</p>
    </form>
  </div>
</template>

<script lang="ts" setup>
import { defineProps, ComputedRef, computed, defineEmits, WritableComputedRef } from "vue";
const emit = defineEmits(['update:height_model', 'update:radius_model'])

// Props
const props = defineProps(['height_model', 'radius_model'])

// Computed
const height: WritableComputedRef<number> = computed({
  get() {
    return props.height_model
  },
  set(value) {
    emit('update:height_model', value)
  }
})
const radius: WritableComputedRef<number> = computed({
  get() {
    return props.radius_model
  },
  set(value) {
    emit('update:radius_model', value)
  }
})
const volume: ComputedRef<string> = computed(() => `${(Math.PI * Math.pow(radius.value, 2) * height.value).toFixed(2)} m²`)
</script>

<style scoped lang="scss">
.form-container {
  display: flex;
  justify-content: center;
  color: #F2CC8F;
  width: 50%;
  font-size: 2rem;

  form {
    width: clamp(320px, 90%, 720px);
    display: flex;
    justify-content: center;
    flex-direction: column;
    box-sizing: border-box;
    padding: 0 48px;
  }

  input {
    height: 48px;
    margin: 6px 0;
  }
}

@media screen and (max-width: 1080px) {
  .form-container {
    width: 100%;
  }
}
</style>
