<template>
  <div class="P P11B">
    <div class="static-page-bg"></div>
  </div>
</template>

<script>
// import VideoPlayer from "@/components/VideoPlayer.vue";

export default {
  components: {},
  data() {
    return {};
  },
  mounted() {},
  methods: {}
};
</script>

<style lang="scss">
@import "@/assets/sass/mixin.scss";

.P11B {
  .static-page-bg {
    width: 100%;
    height: 100%;
    position: absolute;
    left: 0;
    top: 0;
    background: url("../assets/images/011B.jpg") no-repeat 0 0;
    background-size: 100% auto;
  }
}
</style>
