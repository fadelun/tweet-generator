<template>
  <div class="card-names">
    <h2 class="text-2xl font-bold leading-tight">
      {{ user.name ? user.name : "Account name" }}
    </h2>
    <h2 class="font-normal text-2xl text-slate-300 leading-tight">
      {{ user.username ? user.username : "@username" }}
    </h2>
  </div>
</template>
<script setup>
import { inject } from "vue";

const user = inject("user");
</script>
