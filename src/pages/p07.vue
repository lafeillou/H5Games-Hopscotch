<template>
  <div class="P P07">
    <video-player :options="videoOptions" />
    <div class="g-btn g-next-btn" v-hammer:tap="() => {goTo(13)}">Next</div>
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
        poster: "assets/video/poster007.jpg",
        width: document.documentElement.clientWidth - 38,
        sources: [
          {
            src: "assets/video/007.mp4",
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

.P07 {
}
</style>
