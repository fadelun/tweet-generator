<template>
  <div>
    <h2 class="text-2xl font-semibold">
      {{ user.tweet ? user.tweet : "some text" }}
    </h2>
  </div>
</template>
<script setup>
import { inject } from "vue";

const user = inject("user");
</script>
