<script setup lang="ts">
import { reactive } from "vue";
import { useMouse } from "@vueuse/core";

const form = reactive({ name: "" });

const name = ref("");

const { x, y } = useMouse();
</script>

<template>
  <div>
    <CustomModel v-model:name.reverse="form.name"></CustomModel>

    <pre>{{ form }}</pre>

    <BaseInput
      v-model="name"
      label="Name input:"
      type="text"
      class="outlined"
      @blur="name = 'Joseph'"
    >
    </BaseInput>

    <pre>{{ name }}</pre>

    <div>pos: {{ x }}, {{ y }}</div>
  </div>
</template>
