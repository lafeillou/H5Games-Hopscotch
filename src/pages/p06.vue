<template>
  <div class="P P06">
    <video-player :options="videoOptions" />
    <div class="btn01">How to play:the details</div>
    <div class="g-btn g-ready-btn" v-hammer:tap="() => {goTo(12)}">Ready</div>
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
        poster: "assets/video/poster006.jpg",
        width: document.documentElement.clientWidth - 38,
        sources: [
          {
            src: "assets/video/006.mp4",
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

.P06 {
  .btn01 {
    position: absolute;
    @include px2rem(left, 165);
    @include px2rem(top, 32);
    @include px2rem(width, 1000);
    @include px2rem(height, 116);
    font-size: 0;
    background: url("../assets/images/btns/006/f006_btn01.png") no-repeat 0 0;
    background-size: 100% auto;
  }
  // .ready-btn-pos {
  //   @include px2rem(left, 1123);
  //   @include px2rem(top, 619);
  // }
}
</style>
