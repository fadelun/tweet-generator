<template>
  <form class="bg-blue-300 lg:w-1/2 p-5 rounded-xl shadow-xl">
    <div class="input-section mb-4 flex flex-col">
      <label
        class="block mb-2 text-lg font-semibold text-gray-900 dark:text-white"
        for="file_input"
        >Upload image</label
      >
      <input
        class="block w-full text-sm text-gray-900 border border-gray-300 rounded-lg cursor-pointer bg-gray-50 dark:text-gray-400 focus:outline-none dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400"
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
        >Account name</label
      >
      <input
        type="text"
        id="name-input"
        name="account-name"
        v-model="user.name"
        class="bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-blue-500 focus:border-blue-500 block w-full p-2.5 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500"
      />
      <!-- <label for="name-input">Account name :</label>
      <input type="text" name="account-name" v-model="user.name" /> -->
    </div>
    <div class="input-section mb-4 flex flex-col">
      <label
        for="username-input"
        class="block mb-2 text-lg font-semibold text-gray-900 dark:text-white"
        >Username</label
      >
      <div class="flex">
        <span
          class="inline-flex items-center px-3 text-sm text-gray-900 bg-gray-200 border border-r-0 border-gray-300 rounded-l-md dark:bg-gray-600 dark:text-gray-400 dark:border-gray-600"
        >
          @
        </span>
        <input
          type="text"
          v-model="user.username"
          id="username-input"
          class="rounded-none rounded-r-lg bg-gray-50 border border-gray-300 text-gray-900 focus:ring-blue-500 focus:border-blue-500 block flex-1 min-w-0 w-full text-sm p-2.5 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500"
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
        class="block p-2.5 w-full text-sm text-gray-900 bg-gray-50 rounded-lg border border-gray-300 focus:ring-blue-500 focus:border-blue-500 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500"
        placeholder="Leave a tweet..."
      ></textarea>
    </div>
    <!-- <div class="input-section flex flex-col mb-4">
      <label for="date">Date</label>

      <input
        type="date"
        id="date"
        name="timestanmp"
        :value="timestanmp"
        min="2012-01-01"
        :max="timestanmp"
      />
    </div> -->
    <div class="input-section flex flex-col mb-4">
      <ul
        class="items-center w-full text-lg font-semibold text-gray-900 bg-white border border-gray-200 rounded-lg sm:flex dark:bg-gray-700 dark:border-gray-600 dark:text-white"
      >
        <li
          v-for="(device, i) in devices"
          :key="device"
          class="w-full border-b border-gray-200 sm:border-b-0 sm:border-r dark:border-gray-600"
        >
          <div class="flex items-center pl-3">
            <input
              :id="`horizontal-list-${device}`"
              type="radio"
              v-model="user.device"
              :value="`${device == 'kosong' ? ' ' : device}`"
              class="w-4 h-4 text-blue-600 bg-gray-100 border-gray-300 focus:ring-blue-500 dark:focus:ring-blue-600 dark:ring-offset-gray-700 dark:focus:ring-offset-gray-700 focus:ring-2 dark:bg-gray-600 dark:border-gray-500"
            />

            <label
              :for="`horizontal-list-${device}`"
              class="w-full py-3 ml-2 text-md font-medium text-gray-900 dark:text-gray-300"
              >{{ device }}
            </label>
          </div>
        </li>
      </ul>
    </div>
    <div class="input-section flex items-center gap-2 mb-4">
      <input type="checkbox" id="checkbox" v-model="user.verified" />
      <label for="checkbox">Verified account</label>
    </div>

    <button
      type="button"
      class="btn-generate text-white bg-blue-700 hover:bg-blue-800 focus:ring-4 focus:ring-blue-300 font-medium rounded-lg text-sm px-5 py-2.5 mr-2 mb-2 dark:bg-blue-600 dark:hover:bg-blue-700 focus:outline-none dark:focus:ring-blue-800"
    >
      SUBMIT
    </button>
  </form>
</template>
<script setup>
import { ref, onMounted } from "vue";
import html2canvas from "html2canvas";

const props = defineProps(["user", "timestanmp"]);
// const deviceSet = ref("");

const devices = [
  "Twitter Web App",
  "Twitter for Iphone",
  "Twitter for Android",
  "kosong",
];

// const handle = () => {

// }

const uploadImage = (e) => {
  const file = e.target.files[0];
  props.user.image = URL.createObjectURL(file);
};

onMounted(() => {
  const target = document.querySelector(".preview");
  const button = document.querySelector(".btn-generate");

  const generateImage = (e) => {
    e.preventDefault();
    console.log("berhasil");
    html2canvas(target).then((canvas) => {
      const base64image = canvas.toDataURL("image/jpg");
      let anchor = document.createElement("a");
      anchor.setAttribute("href", base64image);
      anchor.setAttribute("download", "my-tweet.jpg");

      anchor.click();
      anchor.remove();
    });
  };

  button.addEventListener("click", generateImage);
});
</script>
