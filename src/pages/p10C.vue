<template>
  <div class="P P10C">
    <video-player :options="videoOptions" />
    <div class="g-btn g-ready-btn" v-hammer:tap="()=> {goTo(22)}">Ready</div>
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
        poster: "assets/video/poster010C.jpg",
        width: document.documentElement.clientWidth - 38,
        sources: [
          {
            src: "assets/video/010C.mp4",
            type: "video/mp4"
          }
        ]
      }
    };
  },
  mounted() {},
  methods: {
    goTo(pageNum) {
      let audio = document.getElementById("music");
      audio.src = "assets/audio/game.mp3";
      audio.play();
      this.$root.eventHub.$emit("goToPage", pageNum);
      // this.$root.eventHub.$emit("cutMusicEvent", "assets/audio/game.mp3");
    }
  }
};
</script>

<style lang="scss">
@import "@/assets/sass/mixin.scss";

.P10C {
}
</style>
