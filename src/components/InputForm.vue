<template>
  <form class="bg-green-200 w-[300] border-black border-2 mt-20 p-5">
    <div class="input-section mb-4 flex flex-col">
      <label for="uplaod-image">Upload image:</label>
      <input type="file" id="uplaod-image" accept="image/jpg, image/png" />
    </div>
    <div class="input-section mb-4 flex flex-col">
      <label for="name-input">Account name and username:</label>
      <input type="text" name="account-name" v-model="user.name" />
      <input type="text" name="username" v-model="user.username" />
    </div>
    <div class="input-section flex flex-col">
      <label for="tweet">write your quote:</label>
      <textarea
        v-model="user.tweet"
        name="tweet"
        id="tweet"
        cols="40"
        rows="4"
      ></textarea>
    </div>
  </form>
</template>
<script setup>
import { inject } from "vue";

const user = inject("user");
</script>
