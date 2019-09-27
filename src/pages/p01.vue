<template>
  <div class="P P01">
    <video-player :options="videoOptions" />
  </div>
</template>

<script>
import VideoPlayer from "@/components/VideoPlayer.vue";
// import $ from "jquery";

export default {
  components: {
    VideoPlayer
  },
  data() {
    return {
      videoOptions: {
        autoplay: true,
        controls: true,
        poster: "assets/video/poster001.jpg",
        width: document.documentElement.clientWidth - 38,
        sources: [
          {
            src: "assets/video/001.mp4",
            type: "video/mp4"
          }
        ]
      }
    };
  },
  mounted() {},
  methods: {}
};
</script>

<style lang="scss">
@import "@/assets/sass/mixin.scss";

.P01 {
}
</style>
