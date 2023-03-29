<script setup>
import InputForm from "./components/InputForm.vue";
import TheCard from "./components/TheCard.vue";

import { reactive, provide } from "vue";

const user = reactive({
  name: "",
  username: "",
  tweet: "",
  image: "",
});

provide("user", user);
</script>

<template>
  <TheCard />
  <InputForm />
</template>
