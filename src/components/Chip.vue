<template>
  <span
    :class="[color]"
    class="
      py-1
      px-2
      h-7
      rounded-lg
      text-white
      font-semibold
      text-sm
      flex
      align-center
      w-max
      cursor-pointer
      active:bg-gray-300
      transition
      duration-300
      ease
    "
  >
    <slot> </slot>
  </span>
</template>
<script lang="ts">
import { defineComponent } from "vue";

export default defineComponent({
  props: ["color"],
});
</script>
