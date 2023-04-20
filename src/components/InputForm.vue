<template>
  <form class="bg-white lg:w-1/2 p-5 rounded-xl shadow-xl">
    <div class="input-section mb-4 flex flex-col">
      <label
        class="block mb-2 text-lg font-semibold text-gray-900 dark:text-white"
        for="file_input"
        >User image</label
      >
      <input
        class="block w-full text-sm text-gray-900 border border-gray-300 rounded-lg cursor-pointer bg-gray-50 dark:text-gray-400 focus:outline-none"
        type="file"
        id="uplaod-image"
        accept="image/*"
        v-on:change="uploadImage"
      />
    </div>
    <div class="input-section mb-4 flex flex-col">
      <label
        for="name-input"
        class="block mb-2 text-lg font-semibold text-gray-900 dark:text-white"
        >Name</label
      >
      <input
        type="text"
        id="name-input"
        name="account-name"
        v-model="user.name"
        class="bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-amber-400 focus:border-amber-400 block w-full p-2.5"
      />
    </div>
    <div class="input-section mb-4 flex flex-col">
      <label
        for="username-input"
        class="block mb-2 text-lg font-semibold text-gray-900 dark:text-white"
        >Username</label
      >
      <div class="flex">
        <span
          class="inline-flex items-center px-3 text-sm text-gray-900 bg-gray-200 border border-r-0 border-gray-300 rounded-l-md"
        >
          @
        </span>
        <input
          type="text"
          v-model="user.username"
          id="username-input"
          class="rounded-none rounded-r-lg bg-gray-50 border border-gray-300 text-gray-900 focus:ring-amber-400 focus:border-amber-400 block flex-1 min-w-0 w-full text-sm p-2.5"
        />
      </div>
    </div>
    <div class="input-section flex flex-col mb-4">
      <label
        for="tweet"
        class="block mb-2 text-lg font-semibold text-gray-900 dark:text-white"
        >Your tweet</label
      >
      <textarea
        id="tweet"
        v-model="user.tweet"
        name="tweet"
        rows="3"
        class="block p-2.5 w-full text-sm text-gray-900 bg-gray-50 rounded-lg border border-gray-300 focus:ring-amber-400 focus:border-amber-400"
        placeholder="Leave a tweet..."
      ></textarea>
    </div>

    <div class="input-section flex flex-col mb-4">
      <ul
        class="items-center w-full text-lg font-semibold text-gray-900 bg-white border border-gray-200 rounded-lg sm:flex"
      >
        <li
          v-for="(device, i) in devices"
          :key="device"
          class="w-full border-b border-gray-200 sm:border-b-0 sm:border-r"
        >
          <div class="flex items-center pl-3">
            <input
              :id="`horizontal-list-${device}`"
              type="radio"
              v-model="user.device"
              :value="`${device == 'kosong' ? ' ' : device}`"
              class="w-4 h-4 text-yellow-300 bg-gray-100 border-gray-300 focus:ring-amber-400"
            />

            <label
              :for="`horizontal-list-${device}`"
              class="w-full py-3 ml-2 text-base font-medium text-gray-900 dark:text-gray-300"
              >{{ device }}
            </label>
          </div>
        </li>
      </ul>
    </div>
    <div class="input-section flex items-center gap-2 mb-4">
      <input type="checkbox" id="checkbox" v-model="user.verified" />
      <label for="checkbox">Verified badge</label>
    </div>

    <button
      type="button"
      class="btn-generate text-white bg-yellow-400 hover:bg-amber-500 focus:ring-4 focus:ring-blue-300 font-medium rounded-lg text-sm px-5 py-2.5 mr-2 mb-2 dark:bg-blue-600 dark:hover:bg-blue-700 focus:outline-none dark:focus:ring-blue-800"
      @click="$emit('modalEvent')"
    >
      Preview
    </button>
  </form>
</template>
<script setup>
import { onMounted } from "vue";
import html2canvas from "html2canvas";

const props = defineProps(["user", "timestanmp"]);

const devices = [
  "Twitter Web App",
  "Twitter for Iphone",
  "Twitter for Android",
  "kosong",
];

const uploadImage = (e) => {
  const file = e.target.files[0];
  props.user.image = URL.createObjectURL(file);
};

onMounted(() => {
  const target = document.querySelector(".preview");
  const button = document.querySelector(".btn-generate");

  const generateImage = (e) => {
    e.preventDefault();

    html2canvas(target).then((canvas) => {
      canvas.style.width = "100%";
      canvas.style.height = "100%";
      const base64image = canvas.toDataURL("image/jpg");
      document.querySelector("#output-preview").appendChild(canvas);

      props.user.url = base64image;
    });
  };

  button.addEventListener("click", generateImage);
});
</script>
