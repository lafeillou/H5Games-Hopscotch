<template>
  <div class="P P01" v-hammer:tap="onTap">
    <video-player :options="videoOptions" />
  </div>
</template>

<script>
import VideoPlayer from "@/components/VideoPlayer.vue";

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
  methods: {
    onTap() {}
  }
};
</script>

<style lang="scss">
@import "@/assets/sass/mixin.scss";

.P01 {
  .vjs-control-bar {
    display: none !important;
  }
}
</style>
