<template>
  <div id="app">
    <!-- <keep-alive>
      <router-view v-if="$route.meta.keepAlive"></router-view>
    </keep-alive>
    <router-view v-if="!$route.meta.keepAlive"></router-view> -->
    <router-view/>
  </div>
</template>

<style lang="less">
@s: 0.0133rem;
#app {
  font-family: "PingFangSC-Medium", "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #000;
  font-size: 28 * @s;
}

textarea::-webkit-input-placeholder,
input::-webkit-input-placeholder {
  /*WebKit browsers*/
  color: #c4cacd;
  line-height: normal;
}
textarea::-moz-input-placeholder,
input::-moz-input-placeholder {
  /*Mozilla Firefox*/
  color: #c4cacd;
  line-height: normal;
}
textarea::-ms-input-placeholder,
input::-ms-input-placeholder {
  /*Internet Explorer*/
  color: #c4cacd;
  line-height: normal;
}
textarea:-webkit-autofill,
input:-webkit-autofill {
  -webkit-box-shadow: 0 0 0 1000px white inset !important;
}
</style>
