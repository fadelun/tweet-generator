<template>
  <div class="card bg-white w-[650px] min-h-[300px] border p-8 rounded-2xl">
    <div class="card-profile w-full flex items-center gap-x-2 mb-4">
      <ProfileImage />
      <UserName />
    </div>
    <div class="card-content">
      <TheQuote />
      <TheDate />
    </div>
  </div>
</template>
<script setup>
import ProfileImage from "./ProfileImage.vue";
import UserName from "./UserName.vue";
import TheQuote from "./TheQuote.vue";
import TheDate from "./TheDate.vue";
</script>
