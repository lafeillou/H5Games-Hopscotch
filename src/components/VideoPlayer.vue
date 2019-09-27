<template>
  <div>
    <video
      webkit-playsinline
      playsinline
      x5-playsinline
      x-webkit-airplay="allow"
      ref="videoPlayer"
      class="video-js"
    ></video>
  </div>
</template>

<script>
import videojs from "video.js";
// import $ from "jquery";

export default {
  name: "VideoPlayer",
  props: {
    options: {
      type: Object,
      default() {
        return {};
      }
    }
  },
  data() {
    return {
      player: null
    };
  },
  mounted() {
    this.player = videojs(this.$refs.videoPlayer, this.options, () => {});
  },
  beforeDestroy() {
    if (this.player) {
      this.player.dispose();
    }
  }
};
</script>