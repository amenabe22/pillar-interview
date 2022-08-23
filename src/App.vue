<template>
  <div class="app font-inter">
    <paywall-comp></paywall-comp>
  </div>
</template>
<script lang="ts">
import { defineComponent } from "vue";
import PaywallComp from "./components/PaywallComp.vue";

export default defineComponent({
  components: { PaywallComp },
});
</script>
