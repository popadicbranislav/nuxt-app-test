<script setup lang="ts">
const { name, nameModifiers } = withDefaults(
  defineProps<{
    name: string;
    nameModifiers?: { capitalize: boolean; reverse: boolean };
  }>(),
  { nameModifiers: () => ({ capitalize: false, reverse: false }) }
);

const emits = defineEmits<{
  (e: "update:name", value: string): void;
}>();

const updateName = (event: Event) => {
  let value = (<HTMLInputElement>event.target).value;

  if (nameModifiers.capitalize) {
    value = value.toUpperCase();
  }

  if (nameModifiers.reverse) {
    value = value.split("").reverse().join("");
  }

  emits("update:name", value);
};
</script>

<template>
  <input :value="name" @input="updateName" />
</template>
