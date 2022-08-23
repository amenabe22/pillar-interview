<template>
  <div class="flex flex-row justify-center items-center bg-black mainbody">
    <div class="flex flex-col items-center mt-10 w-full h-full">
      <img
        class="w-16 rounded-full h-16"
        src="https://res.cloudinary.com/pillario/image/upload/c_thumb,g_custom,w_300,h_300/user-image/page/1a8afd21-5e4c-41e3-a84e-390a2f4fba69?_reload=d3152c70-227d-11ed-ae65-c954ca85930f"
        alt=""
      />
      <div class="flex flex-row pt-2">
        <p class="text-2xl text-white">Ninja</p>
        <svg
          xmlns="http://www.w3.org/2000/svg"
          class="h-5 w-5 text-indigo-500 mt-2"
          viewBox="0 0 20 20"
          fill="currentColor"
        >
          <path
            fill-rule="evenodd"
            d="M6.267 3.455a3.066 3.066 0 001.745-.723 3.066 3.066 0 013.976 0 3.066 3.066 0 001.745.723 3.066 3.066 0 012.812 2.812c.051.643.304 1.254.723 1.745a3.066 3.066 0 010 3.976 3.066 3.066 0 00-.723 1.745 3.066 3.066 0 01-2.812 2.812 3.066 3.066 0 00-1.745.723 3.066 3.066 0 01-3.976 0 3.066 3.066 0 00-1.745-.723 3.066 3.066 0 01-2.812-2.812 3.066 3.066 0 00-.723-1.745 3.066 3.066 0 010-3.976 3.066 3.066 0 00.723-1.745 3.066 3.066 0 012.812-2.812zm7.44 5.252a1 1 0 00-1.414-1.414L9 10.586 7.707 9.293a1 1 0 00-1.414 1.414l2 2a1 1 0 001.414 0l4-4z"
            clip-rule="evenodd"
          />
        </svg>
      </div>
      <p class="text-white">I love video games</p>
      <div class="w-2/5">
        <a
          :href="link.target"
          v-for="(link, ix) in links"
          :key="ix"
          :class="{ 'hover:scale-105 delay-200': ix == 0 }"
          class="
            w-full
            rounded-xl
            my-4
            h-16
            p-3
            bg-white
            hover:ring-cyan-400 hover:ring-2
            flex
            justify-between
          "
        >
          <div v-text="link.logo"></div>
          <div v-text="link.title"></div>
          <div></div>
        </a>
      </div>
      <div class="flex flex-row gap-3 text-white">
        <a href="" v-for="(x, i) in socialmedias" :key="i">
          <img class="w-12 h-12" :src="x.icon" />
        </a>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";

export default defineComponent({
  data: () => ({
    socialmedias: [
      {
        icon: "https://cdn-icons.flaticon.com/png/512/4946/premium/4946005.png?token=exp=1661218588~hmac=4bcc6e523d4d6691a7054effe2610085",
        fb: "fb.com/username",
      },
      {
        icon: "https://cdn-icons-png.flaticon.com/512/1384/1384005.png",
        fb: "fb.com/username",
      },
      {
        icon: "https://cdn-icons-png.flaticon.com/512/3046/3046120.png",
        fb: "fb.com/username",
      },
    ],
    links: [
      {
        logo: "Y",
        title: "Ninja Gaming",
        target: "https://www.youtube.com/ninja",
      },
      {
        logo: "Y",
        title: "Ninja Shorts",
        target: "https://www.youtube.com/ninja",
      },
      {
        logo: "I",
        title: "Instagram",
        target: "https://www.youtube.com/ninja",
      },
      {
        logo: "F",
        title: "Facebook",
        target: "https://www.youtube.com/ninja",
      },
      {
        logo: "T",
        title: "Twitter",
        target: "https://www.youtube.com/ninja",
      },
      {
        logo: "T",
        title: "Twitch",
        target: "https://www.youtube.com/ninja",
      },
      {
        logo: "T",
        title: "TikTok",
        target: "https://www.youtube.com/ninja",
      },
      {
        logo: "T",
        title: "Merch!",
        target: "https://www.youtube.com/ninja",
      },
      {
        logo: "T",
        title: "Text Me",
        target: "https://www.youtube.com/ninja",
      },
      {
        logo: "T",
        title: "Master Class",
        target: "https://www.youtube.com/ninja",
      },
    ],
  }),
});
</script>

<style scoped>
.mainbody {
  background-image: url(https://athlane-file-management-prod.s3.amazonaws.com/8bdd754c-2d5a-4fce-8ddf-e65c3c9f2376?_reload=4bbdaa00-2281-11ed-8a28-df722e6161e6);
  background-repeat: no-repeat;
}
</style>