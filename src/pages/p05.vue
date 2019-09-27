<template>
  <div class="P P05">
    <video-player :options="videoOptions" />
    <div class="g-btn g-yes-btn yes-btn-pos" v-hammer:tap="() => {goTo(12)}">Yes</div>
    <div class="g-btn g-no-btn no-btn-pos" v-hammer:tap="() => {goTo(6)}">No</div>
  </div>
</template>

<script>
import VideoPlayer from "@/components/VideoPlayer.vue";
// import $ from "jquery";

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
        poster: "assets/video/poster005.jpg",
        width: document.documentElement.clientWidth - 38,
        sources: [
          {
            src: "assets/video/005.mp4",
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

.P05 {
  .yes-btn-pos {
    @include px2rem(left, 441);
    @include px2rem(top, 608);
  }
  .no-btn-pos {
    @include px2rem(left, 745);
    @include px2rem(top, 608);
  }
}
</style>
