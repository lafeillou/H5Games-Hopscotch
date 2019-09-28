<template>
  <div class="P P06C">
    <video-player :options="videoOptions" />
    <div class="g-btn back" v-hammer:tap="()=> {goTo(6)}">Back</div>
    <div class="g-btn next" v-hammer:tap="()=> {goTo(10)}">Next</div>
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
        poster: "assets/video/poster006C.jpg",
        width: document.documentElement.clientWidth - 38,
        sources: [
          {
            src: "assets/video/006C.mp4",
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

.P06C {
  .back {
    @include px2rem(width, 170);
    @include px2rem(height, 84);
    background: url("../assets/images/btn_back.png") no-repeat 0 0;
    background-size: 100% auto;
    position: absolute;
    @include px2rem(left, 35);
    @include px2rem(top, 619);
    cursor: pointer;
  }
  .next {
    @include px2rem(width, 170);
    @include px2rem(height, 84);
    background: url("../assets/images/btn_next.png") no-repeat 0 0;
    background-size: 100% auto;
    position: absolute;
    @include px2rem(left, 1123);
    @include px2rem(top, 619);
    cursor: pointer;
  }
}
</style>
