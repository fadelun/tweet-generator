<template>
  <div class="card bg-white w-[450px] min-h-[240px] border p-6 rounded-2xl">
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
