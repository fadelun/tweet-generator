<template>
  <section
    class="preview grid items-center lg:w-1/2 aspect-square p-12 bg-white"
  >
    <section class="twitter-card w-full p-8">
      <div class="card-profile w-full flex items-center gap-x-2 mb-4">
        <img
          id="profile-image"
          class="block mx-auto w-20 h-20 rounded-full sm:mx-0 sm:shrink-0"
          :src="`${user.image ? user.image : 'https://fakeimg.pl/300/'}`"
          alt="user image"
        />
        <div class="card-names">
          <h2 class="text-2xl font-bold leading-tight">
            {{ user.name ? user.name : "Account name" }}
          </h2>
          <h2 class="font-normal text-2xl text-slate-300 leading-tight">
            {{ user.username ? user.username : "@username" }}
          </h2>
        </div>
      </div>
      <div class="card-content">
        <div class="twitter-quote mb-3">
          <h2 class="text-3xl font-normal">
            {{
              user.tweet
                ? user.tweet
                : "Lorem ipsum dolor sit amet consectetur adipisicing elit. Quibusdam totam inventore veritatis, minus repellat fuga vel nostrum assumenda sint alias neque nobis quia voluptate delectus, eaque iste architecto, pariatur consequatur."
            }}
          </h2>
        </div>
        <div class="twitter-date w-full">
          <p class="text-base font-medium">
            <span class="text-slate-400">{{ timestanmp }}</span>
            <span class="text-blue-400"> Twitter Web App</span>
          </p>
        </div>
      </div>
    </section>
  </section>
</template>
<script setup>
import { computed } from "vue";
import moment from "moment"; //library date time

const props = defineProps(["user"]);

const date = new Date();
const timestanmp = computed(() => {
  return moment(date).format("h:mm A · MMM DD, YYYY ·");
});
</script>
