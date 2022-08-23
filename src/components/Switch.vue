<template>
  <label
    for="checked-toggle"
    class="inline-flex relative items-center mb-4 cursor-pointer"
  >
    <input
      @change="$emit('changed', val)"
      v-model="val"
      type="checkbox"
      id="checked-toggle"
      class="sr-only peer"
      checked
    />
    <div
      class="
        w-11
        h-6
        bg-gray-200
        rounded-full
        peer
        peer-checked:after:translate-x-full peer-checked:after:border-white
        after:content-['']
        after:absolute
        after:top-0.5
        after:left-[2px]
        after:bg-white
        after:border-gray-300
        after:border
        after:rounded-full
        after:h-5
        after:w-5
        after:transition-all
        peer-checked:bg-indigo-700
      "
    ></div>
  </label>
</template>
<script lang="ts">
import { defineComponent } from "vue";

export default defineComponent({
  data: () => ({ val: null }),
});
</script>
