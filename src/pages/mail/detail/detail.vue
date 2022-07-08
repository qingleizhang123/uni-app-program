<template>
  <view className='pd20'>
    <view className='bgWhite pd20 card'>
      <view>
        <text className='lg font-weight'>{{ info.head }}:</text>
      </view>

      <view className='ptb20'>
        <text className='lg pl20'>{{ info.content }}</text>
      </view>

      <view className='text-right'>
        <text className='lg'>{{ info.end }}</text>
      </view>

      <view className='text-right'>
        <text className='lg'>{{ createTime }}</text>
      </view>

    </view>
  </view>
</template>

<script setup lang="ts">
const info = {
  head: '亲爱的宝贝',
  content: 'hahahaha',
  end: 'zql',
  createTime: Date.now()
};
</script>

<style>

</style>