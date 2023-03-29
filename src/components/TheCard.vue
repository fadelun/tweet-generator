<template>
  <div class="card bg-white w-[450px] h-[220px] border border-black p-6">
    <div class="card-profile bg-blue-300 w-full flex items-center gap-x-2">
      <ProfileImage />
      <UserName />
    </div>
    <div class="card-content bg-green-300">
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
