<template>
  <div class="P P02" v-hammer:tap="onTap">
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
        // 下面这个需要更换，需要动画团队提供
        poster: "assets/video/poster002.jpg",
        width: document.documentElement.clientWidth - 38,
        sources: [
          {
            src: "assets/video/002.mp4",
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

.P02 {
}
</style>
