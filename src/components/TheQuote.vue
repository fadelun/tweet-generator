<template>
  <div class="twitter-quote mb-3">
    <h2 class="text-2xl font-semibold">
      {{
        user.tweet
          ? user.tweet
          : "Lorem Ipsum dolor sit amet. Aut entuter molestiae "
      }}
    </h2>
  </div>
</template>
<script setup>
import { inject } from "vue";

const user = inject("user");
</script>
