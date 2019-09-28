<template>
  <div>
    <video
      webkit-playsinline
      playsinline
      x5-playsinline
      x-webkit-airplay="allow"
      ref="videoPlayer"
      class="video-js"
      id="video-js"
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
    let that = this;
    this.player = videojs(
      this.$refs.videoPlayer,
      this.options,
      function onPlayerReady() {
        // console.log(this);
        var video = this;
        video.play();
        if (window.WeixinJSBridge) {
          // eslint-disable-next-line
          WeixinJSBridge.invoke(
            "getNetworkType",
            {},
            function() {
              video.play();
            },
            false
          );
        } else {
          document.addEventListener(
            "WeixinJSBridgeReady",
            function() {
              // eslint-disable-next-line
              WeixinJSBridge.invoke("getNetworkType", {}, function() {
                video.play();
              });
            },
            false
          );
        }
        video.on("ended", function() {
          console.log("ended ended");
          that.$root.eventHub.$emit("videoEnded");
        });
      }
    );
  },
  beforeDestroy() {
    if (this.player) {
      this.player.dispose();
    }
  }
};
</script>