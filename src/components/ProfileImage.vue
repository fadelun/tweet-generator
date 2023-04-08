<template>
  <img
    v-if="!user.image"
    id="profile-image"
    class="block mx-auto w-20 h-20 rounded-full sm:mx-0 sm:shrink-0"
    src="https://fakeimg.pl/300/"
    alt="user image"
  />
  <img
    v-else="user.image"
    id="profile-image"
    class="block mx-auto w-20 h-20 rounded-full sm:mx-0 sm:shrink-0"
    :src="user.image"
    alt="user image"
  />
</template>
<script setup>
import { inject } from "vue";

const user = inject("user");
</script>
