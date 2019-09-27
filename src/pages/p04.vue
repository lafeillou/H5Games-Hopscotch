<template>
  <div class="P P04" v-hammer:tap="onTap">
    <video-player :options="videoOptions" />
    <div class="btn01">How to play</div>
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
        poster: "assets/video/poster004.jpg",
        width: document.documentElement.clientWidth - 38,
        sources: [
          {
            src: "assets/video/004.mp4",
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

.P04 {
  .btn01 {
    position: absolute;
    @include px2rem(left, 259);
    @include px2rem(top, 9);
    @include px2rem(width, 768);
    @include px2rem(height, 172);
    font-size: 0;
    background: url("../assets/images/btns/004/f004_btn01.png") no-repeat 0 0;
    background-size: 100% auto;
  }
}
</style>
