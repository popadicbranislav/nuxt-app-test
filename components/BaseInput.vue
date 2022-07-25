<!-- Not needed with multi root components -->
<!-- <script lang="ts">
export default {
  inheritAttrs: false,
};
</script> -->

<script setup lang="ts">
const { label, modelValue } = defineProps<{
  label: string | null;
  modelValue: string | number;
}>();
</script>

<template>
  <label>{{ label }}</label>

  <input
    v-bind="{
        ...$attrs, 
      onInput: (event)=> $emit('update:modelValue', (event?.target as HTMLInputElement).value)}"
    :value="modelValue"
  />
</template>
