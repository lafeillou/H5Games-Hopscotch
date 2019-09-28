<template>
  <div class="P P06">
    <video-player :options="videoOptions" />
    <div class="btn01">How to play:the details</div>
    <div class="step step1" v-hammer:tap="() => {goToDelay(7)}">
      <div class="step-icon step-icon-1"></div>
    </div>
    <div class="step step2" v-hammer:tap="() => {goToDelay(8)}">
      <div class="step-icon step-icon-2"></div>
    </div>
    <div class="step step3" v-hammer:tap="() => {goToDelay(9)}">
      <div class="step-icon step-icon-3"></div>
    </div>
    <div class="step step4" v-hammer:tap="() => {goToDelay(10)}">
      <div class="step-icon step-icon-4"></div>
    </div>
    <div class="step step5" v-hammer:tap="() => {goToDelay(11)}">
      <div class="step-icon step-icon-5"></div>
    </div>
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
    goToDelay(pageNum) {
      setTimeout(() => {
        this.goTo(pageNum);
      }, 500);
    },
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
  .step1 {
    @include px2rem(left, 343 - 5);
    @include px2rem(top, 194 - 5);
    background: url("../assets/images/steps/step1.png") no-repeat 0 0;
  }

  .step2 {
    @include px2rem(left, 752 - 5);
    @include px2rem(top, 194 - 5);
    background: url("../assets/images/steps/step2.png") no-repeat 0 0;
  }

  .step3 {
    @include px2rem(left, 159- 5);
    @include px2rem(top, 427 - 5);
    background: url("../assets/images/steps/step3.png") no-repeat 0 0;
  }

  .step4 {
    @include px2rem(left, 534 - 5);
    @include px2rem(top, 427 - 5);
    background: url("../assets/images/steps/step4.png") no-repeat 0 0;
  }

  .step5 {
    @include px2rem(left, 906 - 5);
    @include px2rem(top, 427 - 5);
    background: url("../assets/images/steps/step5.png") no-repeat 0 0;
  }

  .step-icon-1 {
    @include px2rem(left, 10);
    @include px2rem(top, -35);
    background: url("../assets/images/steps/step1_icon.png") no-repeat 0 0;
  }

  .step-icon-2 {
    @include px2rem(left, 10);
    @include px2rem(top, -35);
    background: url("../assets/images/steps/step2_icon.png") no-repeat 0 0;
  }

  .step-icon-3 {
    @include px2rem(left, 10);
    @include px2rem(top, -35);
    background: url("../assets/images/steps/step3_icon.png") no-repeat 0 0;
  }

  .step-icon-4 {
    @include px2rem(left, 10);
    @include px2rem(top, -35);
    background: url("../assets/images/steps/step4_icon.png") no-repeat 0 0;
  }

  .step-icon-5 {
    @include px2rem(left, 10);
    @include px2rem(top, -35);
    background: url("../assets/images/steps/step5_icon.png") no-repeat 0 0;
  }
}
</style>
