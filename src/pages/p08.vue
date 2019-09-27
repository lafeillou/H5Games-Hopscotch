<template>
  <div class="P P08">
    <video-player :options="videoOptions" />
    <div class="g-btn g-next-btn" v-hammer:tap="() => {goTo(14)}">Next</div>
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
        poster: "assets/video/poster008.jpg",
        width: document.documentElement.clientWidth - 38,
        sources: [
          {
            src: "assets/video/008.mp4",
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

.P08 {
}
</style>
