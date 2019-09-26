<template>
  <div id="app" v-hammer:swipe="onSwipe">
    <P01 v-if="currentPage === 1"></P01>
    <P02 v-if="currentPage === 2"></P02>
    <P03 v-if="currentPage === 3"></P03>
    <P04 v-if="currentPage === 4"></P04>
    <P05 v-if="currentPage === 5"></P05>
    <P06 v-if="currentPage === 6"></P06>
    <P06A v-if="currentPage === 7"></P06A>
    <P06B v-if="currentPage === 8"></P06B>
    <P06C v-if="currentPage === 9"></P06C>
    <P06D v-if="currentPage === 10"></P06D>
    <P06E v-if="currentPage === 11"></P06E>
    <P07 v-if="currentPage === 12"></P07>
    <P08 v-if="currentPage === 13"></P08>
    <P09 v-if="currentPage === 14"></P09>
    <P09A v-if="currentPage === 15"></P09A>
    <P09C v-if="currentPage === 16"></P09C>
    <P10A v-if="currentPage === 17"></P10A>
    <P10B v-if="currentPage === 18"></P10B>
    <P10C v-if="currentPage === 19"></P10C>
    <P11A v-if="currentPage === 20"></P11A>
    <P11B v-if="currentPage === 21"></P11B>
    <P11C v-if="currentPage === 22"></P11C>

    <div id="audio-wrap" style="width:0;height:0;"></div>
    <div class="menu-board-wrap" :class="{isOpen: isOpen}" v-hammer:tap="tapMenu">
      <ul id="menu">
        <li>
          <div class="title" data-index="1">Homepage</div>
        </li>
        <li>
          <div class="title" data-index="4">How to play</div>
        </li>
        <li>
          <div class="title" data-index="6">How to play (the details)</div>
        </li>
        <li>
          <div class="title" data-index="9">Before you start</div>
        </li>
      </ul>
    </div>
    <div class="menu-btn" v-hammer:tap="tapMenu">Menu</div>
  </div>
</template>

<script>
import P01 from "@/pages/p01.vue";
import P02 from "@/pages/p02.vue";
import P03 from "@/pages/p03.vue";
import P04 from "@/pages/p04.vue";
import P05 from "@/pages/p05.vue";
import P06 from "@/pages/p06.vue";
import P06A from "@/pages/p06A.vue";
import P06B from "@/pages/p06B.vue";
import P06C from "@/pages/p06C.vue";
import P06D from "@/pages/p06D.vue";
import P06E from "@/pages/p06E.vue";
import P07 from "@/pages/p07.vue";
import P08 from "@/pages/p08.vue";
import P09 from "@/pages/p09.vue";
import P09A from "@/pages/p09A.vue";
import P09C from "@/pages/p09C.vue";
import P10A from "@/pages/p10A.vue";
import P10B from "@/pages/p10B.vue";
import P10C from "@/pages/p10C.vue";
import P11A from "@/pages/p11A.vue";
import P11B from "@/pages/p11B.vue";
import P11C from "@/pages/p11C.vue";
import $ from "jquery";

export default {
  name: "app",
  data() {
    return {
      isOpen: false,
      currentPage: 1
    };
  },
  components: {
    P01,
    P02,
    P03,
    P04,
    P05,
    P06,
    P06A,
    P06B,
    P06C,
    P06D,
    P06E,
    P07,
    P08,
    P09,
    P09A,
    P09C,
    P10A,
    P10B,
    P10C,
    P11A,
    P11B,
    P11C
  },
  mounted() {
    this.$root.eventHub.$on("goToPage", to => {
      this.currentPage = to;
    });
    window.addEventListener("resize", this.renderResize, false);
    let $app = $("#app");
    let deviceW = document.documentElement.clientWidth - 38;
    let radio = deviceW / 1334;
    $("html").css({ "font-size": 133.4 * radio });
    $app.width(deviceW);
    $app.height((deviceW * 750) / 1334);
    $app.fadeIn(500);
  },
  beforeDestroy() {
    // 移除监听
    window.removeEventListener("resize", this.renderResize, false);
  },
  methods: {
    // selectMenuItem(pageNum) {
    //   this.isOpen = false;
    //   this.$root.eventHub.$emit("goToPage", pageNum);
    // },
    tapMenu(e) {
      console.log(e);
      if (
        e.target.tagName.toLowerCase() === "div" &&
        e.target.className.toLowerCase() === "title"
      ) {
        this.$root.eventHub.$emit("goToPage", $(e.target).data("index"));
        return;
      }
      this.isOpen = !this.isOpen;
    },
    onSwipe(event) {
      // 从右向左滑动
      if (event.direction === 2) {
        if (this.currentPage < 22) {
          this.currentPage++;
        } else {
          this.currentPage = 1;
        }
        // 从左向右滑动
      } else if (event.direction === 4) {
        if (this.currentPage > 1) {
          this.currentPage--;
        }
      }
    },
    // 判断是否横屏
    renderResize() {
      this.$nextTick(() => {
        // 判断横竖屏
        // let width = document.documentElement.clientWidth;
        // let height = document.documentElement.clientHeight;
        // if (width > height) {
        //   location.reload();
        // }
        location.reload();
      });
    }
  }
};
</script>

<style lang="scss" >
html,
body {
  // height: 100%;
  background-color: #000;
}
@import "./assets/sass/mixin.scss";
@font-face {
  font-family: "webfont";
  font-display: swap;
  src: url("/assets/font/webfont.eot"); /* IE9 */
  src: url("/assets/font/webfont.eot?#iefix") format("embedded-opentype"),
    /* IE6-IE8 */ url("/assets/font/webfont.woff2") format("woff2"),
    url("/assets/font/webfont.woff") format("woff"),
    /* chrome、firefox */ url("/assets/font/webfont.ttf") format("truetype"),
    /* chrome、firefox、opera、Safari, Android, iOS 4.2+*/
      url("/assets/font/webfont.svg#webfont") format("svg"); /* iOS 4.1- */
}

.web-font {
  font-family: "webfont" !important;
  font-size: 16px;
  font-style: normal;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
#app {
  display: none;
  @include px2rem(height, 750);
  @include px2rem(width, 1334);
  position: relative;
  overflow: hidden;
  // background: #000 url("/assets/images/bg.png") no-repeat center center;
  background-size: 100% auto;
  .P {
    width: 100%;
    height: 100%;
  }
  .indexPageFontSize {
    position: absolute;
    left: 50%;
    @include px2rem(bottom, 30);
    @include px2rem(margin-left, -55);
    color: #fff;
    font-weight: bold;
    @include px2rem(font-size, 30);
  }

  .menu-board-wrap {
    position: absolute;
    height: 100%;
    width: 100%;
    display: none;
    background-color: transparent;
    // @include px2rem(left, -409);
    overflow-y: auto;
    top: 0;
    transition: left 0.3s;
    &.isOpen {
      display: block;
    }
    > ul {
      display: inline-block;
      @include px2rem(margin-left, 150);
      @include px2rem(margin-top, 35);
      > li {
        width: 100%;

        > div.title {
          @include px2rem(height, 53);
          text-indent: -9999999px;
        }
        // text-indent: -999999px;
        &:nth-child(1) {
          > div.title {
            background: url("./assets/images/step01_bg.png") no-repeat 0 0;
            background-size: 100% auto;
          }
          @include px2rem(width, 221);
        }
        &:nth-child(2) {
          > div.title {
            background: url("./assets/images/step02_bg.png") no-repeat 0 0;
            background-size: 100% auto;
          }
          @include px2rem(width, 235);
        }
        &:nth-child(3) {
          > div.title {
            background: url("./assets/images/step03_bg.png") no-repeat 0 0;
            background-size: 100% auto;
          }
          @include px2rem(width, 411);
        }
        &:nth-child(4) {
          > div.title {
            background: url("./assets/images/step04_bg.png") no-repeat 0 0;
            background-size: 100% auto;
          }
          @include px2rem(width, 296);
        }
      }
    }
  }
  .menu-btn {
    position: absolute;
    @include px2rem(left, 20);
    @include px2rem(top, 20);
    @include px2rem(width, 114);
    @include px2rem(height, 80);
    background: url("./assets/images/menu_bg.png") no-repeat 0 0;
    background-size: 100% 100%;

    text-indent: -9999999px;
  }
  // 播放按钮的大小和位置
  .video-js {
    .vjs-big-play-button {
      @include px2rem(width, 200);
      border-radius: 50%;
      @include px2rem(height, 200);
      @include px2rem(line-height, 200);
      @include px2rem(font-size, 100);
      top: 50%;
      left: 50%;
      @include px2rem(margin-top, -100);
      @include px2rem(margin-left, -100);
    }
  }
}
</style>
