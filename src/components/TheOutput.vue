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
        @click="$emit('closeEvent')"
      >
        ✖
      </span>
    </div>
    <button
      class="btn-dowload px-6 py-2 text-base md:px-10 md:py-3 rounded-md md:text-xl font-medium text-white bg-blue-500"
    >
      Download
    </button>
  </section>
</template>
<script setup>
import { onMounted } from "vue";
import html2canvas from "html2canvas";

onMounted(() => {
  const target = document.getElementById("output-preview");
  const button = document.querySelector(".btn-dowload");

  const downloadImage = (e) => {
    e.preventDefault();
    console.log("berhasil");
    html2canvas(target).then((canvas) => {
      console.log(canvas);
      const base64image = canvas.toDataURL("image/jpg");
      let anchor = document.createElement("a");
      anchor.setAttribute("href", base64image);
      anchor.setAttribute("download", "my-tweet.jpg");

      anchor.click();
      anchor.remove();
    });
  };

  button.addEventListener("click", downloadImage);
});
</script>
