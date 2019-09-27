<template>
  <div class="P P09">
    <video-player :options="videoOptions" />
    <div class="g-btn g-level-btn level1" v-hammer:tap="() => {goTo(15)}">Level1</div>
    <div class="g-btn g-level-btn level2" v-hammer:tap="() => {goTo(18)}">Level2</div>
    <div class="g-btn g-level-btn level3" v-hammer:tap="() => {goTo(16)}">Level3</div>
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
        poster: "assets/video/poster009.jpg",
        width: document.documentElement.clientWidth - 38,
        sources: [
          {
            src: "assets/video/009.mp4",
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

.P09 {
  .level1 {
    background: url("../assets/images/btn_level_1.png") no-repeat 0 0;
    background-size: 100% auto;
    @include px2rem(left, 879);
    @include px2rem(top, 401);
  }
  .level2 {
    background: url("../assets/images/btn_level_2.png") no-repeat 0 0;
    background-size: 100% auto;
    @include px2rem(left, 879);
    @include px2rem(top, 499);
  }
  .level3 {
    background: url("../assets/images/btn_level_3.png") no-repeat 0 0;
    background-size: 100% auto;
    @include px2rem(left, 879);
    @include px2rem(top, 596);
  }
}
</style>
