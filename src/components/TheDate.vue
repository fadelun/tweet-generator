<template>
  <div class="twitter-date w-full">
    <p class="text-base font-medium">
      <span class="text-slate-400">{{ timestanmp }}</span>
      <span class="text-blue-400"> Twitter Web App</span>
    </p>
  </div>
</template>
<script setup>
import { computed } from "vue";

import moment from "moment";

const date = new Date();
const timestanmp = computed(() => {
  return moment(date).format("h:mm A · MMM DD, YYYY ·");
});
</script>
