<script setup>
import InputForm from "./components/InputForm.vue";
import TheCard from "./components/TheCard.vue";
import TheOutput from "./components/TheOutput.vue";

import { ref, computed, reactive } from "vue";
import moment from "moment"; //library date time

const showModal = ref(false);

const user = reactive({
  name: "",
  username: "",
  tweet: "",
  image: "",
  device: "",
  verified: true,
  url: "",
});

const date = new Date();
const timestanmp = computed(() => {
  return moment(date).format("h:mm A · MMM DD, YYYY ·");
});
</script>

<template>
  <div class="container mx-auto flex justify-center items-center relative">
    <TheCard :user="user" :timestanmp="timestanmp" />
    <InputForm :user="user" @modal-event="showModal = true" />
    <teleport to="#modal-root" v-if="showModal">
      <TheOutput :user="user" @modal-event="showModal = false" />
    </teleport>
  </div>
</template>

<!-- problem
  - nama akun dan username pindah posisi 
-->
