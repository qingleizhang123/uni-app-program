<template>
  <view className="auth">
    <view className="mt100">
      <view className="row row__justify--center">
        <view className="col-10 text-center">
          <image className="wd100" :src="logo" mode="widthFix"></image>
        </view>
      </view>
      <view className="row row__justify--center mt350">
        <view className="col-8 text-center">
          <button type="primary" openType="getUserInfo">微信授权登陆</button>
        </view>
      </view>
    </view>
  </view>
</template>

<script setup lang="ts">
import logo from '../../../static/imgs/logo.png';

const getUserInfo = () {

};
</script>

<style lang="scss">
@import "../../../static/css/mixn";
page {
  background: $color-ec;
}
</style>