<script setup lang="ts">
import { ArrowUpRight } from "lucide-vue-next";
interface Props {
  text: string;
  href?: string;
  disabled?: boolean;
  type?: "button" | "submit";
}

withDefaults(defineProps<Props>(), {
  type: "button",
  disabled: false,
});
</script>

<template>
  <div class="relative inline-block">
    <a
      v-if="href"
      :href="href"
      class="group relative flex items-center justify-center px-10 py-5 bg-[#1E3A8A] text-white font-bold rounded-full overflow-hidden transition-all duration-500 hover:pr-14 shadow-sm"
    >
      <span class="relative z-10 transition-colors duration-500">{{
        text
      }}</span>
      <ArrowUpRight
        class="absolute right-6 opacity-0 group-hover:opacity-100 transition-all duration-500 transform translate-x-4 group-hover:translate-x-0 w-5 h-5"
      />
      <div
        class="absolute inset-0 bg-accent-red scale-y-0 group-hover:scale-y-100 origin-bottom transition-transform duration-500 ease-out"
      ></div>
    </a>

    <button
      v-else
      :type="type"
      :disabled="disabled"
      class="group relative flex items-center justify-center px-10 py-5 bg-[#1E3A8A] text-white font-bold rounded-full overflow-hidden transition-all duration-500 disabled:opacity-50 disabled:cursor-not-allowed shadow-sm"
    >
      <span class="relative z-10">{{ text }}</span>
      <div
        class="absolute inset-0 bg-accent-red scale-y-0 group-hover:scale-y-100 origin-bottom transition-transform duration-500 ease-out"
      ></div>
    </button>
  </div>
</template>
