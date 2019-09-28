<template>
  <div class="P P09C" v-hammer:tap="onTap">
    <video-player :options="videoOptions" />
    <div class="g-btn g-ok-btn" v-hammer:tap="() => {goTo(19)}">OK</div>
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
        poster: "assets/video/poster009C.jpg",
        width: document.documentElement.clientWidth - 38,
        sources: [
          {
            src: "assets/video/009C.mp4",
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

.P09C {
}
</style>
