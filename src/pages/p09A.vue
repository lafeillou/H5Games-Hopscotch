<template>
  <div class="P P09A">
    <video-player :options="videoOptions" />
    <div class="g-btn g-ok-btn" v-hammer:tap="() => {goTo(17)}">OK</div>
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
        poster: "assets/video/poster009A.jpg",
        width: document.documentElement.clientWidth - 38,
        sources: [
          {
            src: "assets/video/009A.mp4",
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

.P09A {
}
</style>
