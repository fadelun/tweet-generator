<template>
  <div class="card-names">
    <h2 class="text-xl font-semibold">
      {{ user.name ? user.name : "Account name" }}
    </h2>
    <h2 class="font-semibold text-sm text-slate-300">
      {{ user.username ? user.username : "@username" }}
    </h2>
  </div>
</template>
<script setup>
import { inject } from "vue";

const user = inject("user");
</script>
