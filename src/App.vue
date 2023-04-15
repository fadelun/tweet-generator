<script setup>
import InputForm from "./components/InputForm.vue";
import TheCard from "./components/TheCard.vue";

import { computed, reactive } from "vue";
import moment from "moment"; //library date time

const user = reactive({
  name: "",
  username: "",
  tweet: "",
  image: "",
  device: "",
  verified: true,
});

const date = new Date();
const timestanmp = computed(() => {
  return moment(date).format("h:mm A · MMM DD, YYYY ·");
});
</script>

<template>
  <div class="container mx-auto flex flex-col lg:flex-row xl:gap-x-24">
    <TheCard :user="user" :timestanmp="timestanmp" />
    <InputForm :user="user" />
  </div>
</template>

<!-- problem
  - gambar profile tidak object fit
  - nama akun dan username pindah posisi 


-->
