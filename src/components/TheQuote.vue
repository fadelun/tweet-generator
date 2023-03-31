<template>
  <div class="twitter-quote mb-3">
    <h2 class="text-3xl font-semibold">
      {{
        user.tweet
          ? user.tweet
          : "Here’s an idea 🤔 do something good for someone and don’t post about it on social media. "
      }}
    </h2>
  </div>
</template>
<script setup>
import { inject } from "vue";

const user = inject("user");
</script>
