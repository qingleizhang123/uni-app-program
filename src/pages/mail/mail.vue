<template>
  <view>
    <view className="pd20" v-for="(item, index) in mail" :key="index">
      <view :class="`pd20 bg-gradual-${item.color} card`" @click="goDetail(item)">

        <view className='row'>
          <view className='col-9'>
            <view className='row'>
              <view className='col-1' v-for="(zip, index) in PAGE.ZIP_CODE" :key="index">
                <view className='zipCode bgWhite text-center'>
                  <text className='lg font-weight black'>{{ zip }}</text>
                </view>
              </view>
            </view>

            <view className='mt20'>
              <text className='lg font-weight black'>{{ item.head }}</text>
              <text className='lg font-weight black pl10 '>(收)</text>
            </view>
            <view>
              <text className='sm black'>{{ item.createTime }}</text>
            </view>
          </view>


          <view className='col-3 flex-right rel'>
            <view className='stampImg'>
              <image className='wd100' mode='widthFix' lazyLoad  :src="item.stamp"/>
            </view>
          </view>
        </view>
      </view>
    </view>
    <view v-if="mail.length === 0" className="pd20">
      <template v-if="loading">
        <loadMore status="loading"></loadMore>
      </template>
      <template v-else>
        <loadMore status="no-more" :contentText="contentText"></loadMore>
      </template>
    </view>
    <view v-if="mail.length > 0">
      <loadMore v-if="loading" status="loading"></loadMore>
    </view>
    <!--浮动按钮-->
    <view className='floatFab'>
      <view className='bg-gradual-green fb-icon'  @click="isPlus()">
        <text className='at-icon at-icon-add'></text>
      </view>
    </view>
  </view>
</template>

<script setup lang="ts">
import { ref } from 'vue';
import loadMore from '@dcloudio/uni-ui/lib/uni-load-more/uni-load-more.vue';
import { PAGE } from "../../utils/constant";
const isShowPlus = false;
const param = {
};
const mail = ref([]);
const loading = ref(false);
const contentText = {
  contentdown: '查看更多',
  contentrefresh: '加载中',
  contentnomore: '暂时没有来信~'
}

const getMail = () => {};

// 新增
const isPlus = () => {
  uni.navigateTo({
    url: '/pages/mail/edit/edit',
  });
}

// 信件详情
const goDetail = () => {
  
}
</script>

<style lang="scss">

.floatFab {
  position: fixed;
  bottom: 50px;
  right: 30px;
  z-index: 1000;
}
.zipCode {
  width: 35px;
  height: 35px;
  line-height: 35px;
  border-radius: 10px;
}

.stamp {
  width: 180px;
  height: 120px;
  line-height: 120px;
}

.stampImg {
  left: 0;
  right: 0;
  top: 0;
  width: 100%;
  z-index: 1000;
}

image {
  height: 100px;
}
</style>