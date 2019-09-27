<template>
  <div class="P P10B">
    <video-player :options="videoOptions" />
    <div class="g-btn g-ready-btn" v-hammer:tap="() => {goTo(20)}">Ready</div>
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
        controls: false,
        // 下面这个需要更换，需要动画团队提供
        poster: "assets/video/poster010B.jpg",
        width: document.documentElement.clientWidth - 38,
        sources: [
          {
            src: "assets/video/010B.mp4",
            type: "video/mp4"
          }
        ]
      }
    };
  },
  mounted() {},
  methods: {
    goTo(pageNum) {
      this.$root.eventHub.$emit("goToPage", pageNum);
    }
  }
};
</script>

<style lang="scss">
@import "@/assets/sass/mixin.scss";

.P10B {
}
</style>
