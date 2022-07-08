<template>
  <view v-if="!isNext" className='pd20 rel' :style="height">
    <view className='bgWhite card ht100 shadow-lg'>
      <view className='plr20 pt20'>
        <view className='row'>
          <view className='col-8'>
            <input
              name='value'
              type='text'
              placeholder='说点什么吧'
              :value="param.head"
              @input="onInputChange($event, 'param', 'head')"
            />
          </view>
          <view className='col-4 flex-right'>
            <view className='wx wx-next weak' @click="toNext()" style='font-size:25Px' />
          </view>
        </view>
      </view>
      <view className='plr20'>
        {{ Line }}
      </view>
      <view className='pd20'>
        <textarea
          :value="param.content"
          maxLength="1000"
          @input="ontextAreaChange(this, 'param', 'content')"
          autoFocus
          height="800"
          placeholder='你想对TA说...'
        />
      </view>
      <view className='plr20'>
        <view className='row'>
          <view className='col-8'>
          </view>
          <view className='col-4'>
            <input
              name='value'
              type='text'
              placeholder='说点什么吧'
              :value="param.end"
              @input="onInputChange(this, 'param', 'head')"
            />
          </view>
        </view>
      </view>
    </view>
  </view>
  <view v-if="isNext" className='pd20'>
    <!--信封-->
    <view :class="`pd20 bg-gradual-${param.color} card`" style='height:150px;'>

      <view className='row' style='height:60px'>
        <view className='col-1' v-for="(item, index) in zipCode" :key="index">
          <view className='zipCode bgWhite card text-center'>
            <text className='lg font-weight black'>{{ item }}</text>
          </view>
        </view>
        <view className='col-3 col__offset-2 flex-right rel'>
          <view v-if="param.stamp" className='stampImg'>
            <image className='wd100' mode='widthFix' lazyLoad :src="param.stamp" />
          </view>
          <view v-if="!param.stamp" className='stamp bgWhite card text-center' ><text className='sm muted'>贴邮票处</text></view>

        </view>
      </view>

      <view>
        <view className='pl30'>
          <text className='xxl font-weight black'>{{ param.head }}</text>
          <text className='xxl font-weight black pl10 '>(收)</text>
        </view>
      </view>
      <view className='mt70'>
        <view className='text-right'>
          <text className='sm font-weight black'>{{ param.end }}</text>
          <text className='sm font-weight black pl10 '>(寄)</text>
        </view>
      </view>
    </view>
    <!--选择邮票-->
    <view className='ptb20'>
      <view>
        <text className='lg font-weight'>选择邮票</text>
      </view>
      <scroll-view scroll-x="true">
        <view className='row'>
          <view className='col-4' v-for="(item, index) in PAGE.STAMP" :key="index">
            <view className='pd10' @click="selectStamp(item)">
              <image className='wd100' mode='widthFix' lazyLoad :src="item" />
            </view>
          </view>
        </view>
      </scroll-view>
    </view>\
    <!--选择封面颜色-->
    <view className='ptb20'>
      <view>
        <text className='lg font-weight'>选择封面颜色</text>
      </view>
      <view className='ptb20'>
        <view className='row row--wrap'>
          <view className='col-1' v-for="(item, index) in PAGE.COLOR" :key="index">
            <view @click="selectColor(item)" :className="`zipCode bg-gradual-${item} card`"/>
          </view>
        </view>
      </view>
    </view>
    <!--按钮-->
    <view>
      <button type='primary' @lick="send()" >寄出</button>
    </view>
  </view>
</template>

<script setup lang="ts">
import { ref } from 'vue';
const zipCode = ['5','2','0','1','3','1','4'] ;
const isNext = ref(false);
const param = {
  color: 'primary',
  head: '亲爱的宝贝',
  end: 'zql'
};

const toNext = () => {
  isNext.value = true;
  // 跳转
};

// 选择邮票
const selectStamp = (item) => {
  param.stamp = item;
};

// 选择颜色
const selectColor = (item) => {
  param.color = item;
};

// 寄出
const send = () => {

};

const onInputChange = () => {

};
</script>

<style lang="scss" scoped>

page {
  overflow-y: hidden;
  height: 100%;
}

.rel {
  height: 100%;
}

.at-input input {
  padding: 8px;
}

.at-textarea {
  border: none;
}

.zipCode {
  width: 50px;
  height: 50px;
  line-height: 50px;
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

</style>