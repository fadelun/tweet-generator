<template>
  <section
    class="preview grid items-center lg:w-1/2 aspect-square p-4 sm:p-10 md:p-12 bg-white shadow-xl"
  >
    <section class="twitter-card w-full p-8">
      <div class="card-profile w-full flex items-center gap-x-4 mb-4">
        <img
          id="profile-image"
          class="block mx-auto w-12 h-12 sm:w-20 sm:h-20 rounded-full sm:mx-0 sm:shrink-0"
          :src="`${user.image ? user.image : 'https://fakeimg.pl/300/'}`"
          alt="user image"
        />
        <div class="card-names w-full">
          <h2
            class="text-lg sm:text-2xl font-bold leading-tight flex gap-1 items-center"
          >
            <span> {{ user.name ? user.name : "Account name" }}</span
            ><span
              ><img
                v-if="user.verified"
                :src="verified"
                alt="verified image"
                class="w-[40%] sm:w-[60%] md:w-[70%]"
            /></span>
          </h2>
          <h2
            class="font-normal text-sm sm:text-xl text-slate-400 leading-tight"
          >
            {{ user.username ? `@${user.username}` : "@username" }}
          </h2>
        </div>
      </div>
      <div class="card-content">
        <div class="twitter-quote mb-3">
          <h2 class="text-xl sm:text-3xl font-normal">
            {{
              user.tweet
                ? user.tweet
                : "Lorem ipsum dolor sit amet consectetur adipisicing elit. Quibusdam totam inventore veritatis, minus repellat fuga vel nostrum assumenda sint alias neque nobis quia voluptate delectus, eaque iste architecto, pariatur consequatur."
            }}
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
const props = defineProps(["user", "timestanmp"]);
</script>
