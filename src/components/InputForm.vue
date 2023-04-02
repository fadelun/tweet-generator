<template>
  <form
    class="absolute b-0 bg-green-200 w-[300] border-black border-2 mt-20 p-5"
  >
    <div class="input-section mb-4 flex flex-col">
      <label for="uplaod-image">Upload image:</label>
      <input type="file" id="uplaod-image" accept="image/jpg, image/png" />
    </div>
    <div class="input-section mb-4 flex flex-col">
      <label for="name-input">Account name :</label>
      <input type="text" name="account-name" v-model="user.name" />
    </div>
    <div class="input-section mb-4 flex flex-col">
      <label for="name-input">username:</label>
      <input type="text" name="username" v-model="user.username" />
    </div>
    <div class="input-section flex flex-col mb-4">
      <label for="tweet">write your quote:</label>
      <textarea
        v-model="user.tweet"
        name="tweet"
        id="tweet"
        cols="40"
        rows="2"
      ></textarea>
    </div>
    <a
      class="btn-generate block w-full h-20 text-center py-2 px-4 bg-blue-300 rounded-sm"
    >
      SUBMIT
    </a>
  </form>
</template>
<script setup>
import { inject, onMounted, onUnmounted } from "vue";
import html2canvas from "html2canvas";

const user = inject("user");
onMounted(() => {
  const target = document.querySelector(".twitter-card");
  const button = document.querySelector(".btn-generate");
  const generateImage = (e) => {
    e.preventDefault();
    console.log("berhasil");
    html2canvas(target).then((canvas) => {
      const base64image = canvas.toDataURL("image/png");
      let anchor = document.createElement("a");
      anchor.setAttribute("href", base64image);
      anchor.setAttribute("download", "my-tweet.png");
      anchor.click();
      anchor.remove();
    });
  };

  // masih banyak error di console

  button.addEventListener("click", generateImage);
});

// onUnmounted(() => {
//   anchor.remove();
// });
</script>
