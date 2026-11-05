<script setup>
defineProps({
  modelValue: { type: String, required: true },
  options: { type: Array, required: true },
});

defineEmits(["update:modelValue"]);
</script>

<template>
  <select
    :value="modelValue"
    aria-label="Сортировка товаров"
    class="border pl-3 bg-white border-gray-500/30 h-[52px] rounded-md outline-none"
    @change="$emit('update:modelValue', $event.target.value)"
  >
    <option
      v-for="option in options"
      :key="option.value"
      :value="option.value"
    >
      {{ option.label }}
    </option>
  </select>
</template>