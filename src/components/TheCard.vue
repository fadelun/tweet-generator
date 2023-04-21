<template>
  <section
    class="preview grid items-center w-4/5 lg:w-1/2 aspect-square p-4 sm:p-10 md:p-12 bg-white shadow-xl absolute top-[-100rem]"
  >
    <section class="twitter-card w-full p-8">
      <div class="card-profile w-full flex gap-x-2 sm:gap-x-4 mb-4">
        <div
          class="image-contain block mx-auto w-12 h-12 sm:w-20 sm:h-20 sm:mx-0 shrink-0"
        >
          <img
            id="profile-image"
            class="align-middle rounded-full w-12 h-12 sm:w-20 sm:h-20"
            :src="`${user.image ? user.image : fakeImage}`"
            alt="user image"
          />
          <!-- fit object tidak support di html2canvas -->
        </div>

        <div class="card-names w-full">
          <h2 class="text-lg sm:text-2xl font-bold flex gap-1 items-center">
            {{ user.name ? user.name : "Account name" }}

            <span class="relative w-8">
              <img
                v-if="user.verified"
                :src="verified"
                alt="verified image"
                class="w-[40%] sm:w-[60%] md:w-[70%] absolute -bottom-3 lg:-bottom-5"
            /></span>
          </h2>
          <h2 class="font-normal text-sm sm:text-xl text-slate-400">
            {{ user.username ? `@${user.username}` : "@username" }}
          </h2>
        </div>
      </div>
      <div class="card-content">
        <div class="twitter-quote mb-3">
          <h2 class="text-xl sm:text-3xl font-normal">
            {{ user.tweet ? user.tweet : "Leave a tweet" }}
          </h2>
        </div>
        <div class="twitter-date w-full">
          <p class="text-xs sm:text-base font-medium">
            <span class="text-slate-400">{{ timestanmp }}</span>
            <span class="text-blue-400"> {{ user.device }}</span>
          </p>
        </div>
      </div>
    </section>
  </section>
</template>
<script setup>
import verified from "../assets/verified.svg";
import fakeImage from "../assets/fake-image.png";
const props = defineProps(["user", "timestanmp"]);
</script>
