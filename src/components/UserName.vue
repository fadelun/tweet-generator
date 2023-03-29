<template>
  <div class="card-names">
    <h2 class="text-xl font-semibold">{{ name }}</h2>
    <h2 class="font-semibold">{{ username }}</h2>
  </div>
</template>
<script setup>
import { inject } from "vue";

const user = inject("user");

const { name, username } = user;
</script>
