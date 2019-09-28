<template>
  <div class="P P11A">
    <div class="static-page-bg"></div>
  </div>
</template>

<script>
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

.P11A {
  .static-page-bg {
    width: 100%;
    height: 100%;
    position: absolute;
    left: 0;
    top: 0;
    background: url("../assets/images/011A.jpg") no-repeat 0 0;
    background-size: 100% auto;
  }
}
</style>
