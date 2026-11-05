<script setup>
import { onBeforeUnmount, ref, watch } from "vue";

const props = defineProps({
  modelValue: { type: String, default: "" },
  placeholder: { type: String, default: "Поиск..." },
});

const emit = defineEmits(["update:modelValue"]);

const inputQuery = ref(props.modelValue);

let debounceTimeout = null;

watch(inputQuery, (newVal) => {
  clearTimeout(debounceTimeout);

  if (newVal === props.modelValue) {
    return;
  }

  if (!newVal.trim()) {
    emit("update:modelValue", "");
    return;
  }

  debounceTimeout = setTimeout(() => {
    emit("update:modelValue", newVal);
  }, 300);
});

watch(
  () => props.modelValue,
  (newVal) => {
    if (newVal !== inputQuery.value) {
      clearTimeout(debounceTimeout);
      inputQuery.value = newVal;
    }
  },
);

const clearSearch = () => {
  clearTimeout(debounceTimeout);
  inputQuery.value = "";
  emit("update:modelValue", "");
};

onBeforeUnmount(() => {
  clearTimeout(debounceTimeout);
});
</script>

<template>
  <div
    class="flex items-center border px-3 gap-2 bg-white border-gray-500/30 h-[52px] rounded-md"
  >
    <img src="/search-icon.svg" alt="" class="w-5 h-5 shrink-0" />

    <input
      v-model="inputQuery"
      type="text"
      :placeholder="placeholder"
      aria-label="Поиск товаров"
      class="w-full h-full outline-none text-gray-500 placeholder-gray-500 text-sm"
    />

    <button
      v-if="inputQuery"
      type="button"
      class="cursor-pointer"
      aria-label="Очистить поиск"
      @click="clearSearch"
    >
      &times;
    </button>
  </div>
</template>