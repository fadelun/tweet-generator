<template>
  <section
    id="output"
    class="fixed inset-0 bg-[#0000003b] flex justify-center items-center flex-col"
  >
    <div
      id="output-preview"
      class="mb-4 w-80 h-80 sm:w-[440px] sm:h-[440px] lg:w-[620px] lg:h-[620px]"
    >
      <span
        class="absolute top-2 right-4 text-lg md:top-4 md:right-6 md:text-5xl hover:cursor-pointer"
        @click="$emit('modalEvent')"
      >
        ✖
      </span>
    </div>
    <a
      :href="user.url"
      download="my-tweet.jpg"
      class="btn-dowload px-6 py-2 text-base md:px-10 md:py-3 rounded-md md:text-xl font-medium text-white bg-blue-600 hover:bg-blue-800"
    >
      Download
    </a>
  </section>
</template>
<script setup>
const props = defineProps(["user"]);
</script>
