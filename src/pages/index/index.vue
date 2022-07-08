<template>
  <view class="index">
    <!--头部-->
    <view className="pd20">
      <view className='pd20 card rel' style='opacity: 0.8;'>
        <image className='wd100 ht100 common-bg card' :src="PAGE.BG.HOME" />
        <view className='row row__align--center'>
          <view className='col-3 text-center'>
            <image className='avatar-normal' :src="user.avatarUrl" />
            <view>
              <text className='lg'>{{ user.nickName }}</text>
            </view>

          </view>
          <view className='col-6 text-center'>
            <view>
              <text className='lg font-weight'>我们在一起</text>
            </view>
            <view>
              <text className='xxl plr20 brand font-weight'>{{ together }}</text>
              <text className='lg'>天</text>
            </view>
          </view>
          <view className='col-3 text-center'>
            <view v-if="isBind">
              <image className='avatar-normal' :src="bindUser.avatarUrl" />
              <view>
                <text className='lg'>{{ bindUser.nickName }}</text>
              </view>
            </view>
            <view v-if="!isBind">
              <button type='primary' className='noCssBtn' openType='share' >
                  <view className='wx wx-plus-b white' style='font-size:40Px' />
              </button>
              <view>
                <text className='sm'>邀请TA吧</text>
              </view>
            </view>
          </view>
        </view>
        <image className='gif-wave' lazyLoad :src="wave" mode='scaleToFill' />
      </view>
      <view class="order bgWhite"></view>
    </view>

    <!--功能部分-->
    <view className='pd20'>
      <view className='row row-wrap'>
        <view className='col-6'>
          <view className='pr10' @click="goview('remember')">
            <view className='row row__align--center bgWhite card shadow-lg'>
              <view className='col-7'>
                <view className='pd20'>
                  <view className='pd10'>
                    <text className='lg font-weight'>纪念日</text>
                  </view>
                  <view className='pd10'>
                    <text className='xxl major font-weight pr10'>{{ count.remember }}</text>
                    <text className='lg weak'>个</text>
                  </view>
                </view>
              </view>
              <view className='col-5 text-center'>
                <image className='iconSize' :src="date"/>
              </view>
            </view>
          </view>
        </view>
        <view className='col-6'>
          <view className='pl10' @click="goview('todo')">
            <view className='row row__align--center bgWhite card shadow-lg'>
              <view className='col-7'>
                <view className='pd20'>
                  <view className='pd10'>
                    <text className='lg font-weight'>愿望清单</text>
                  </view>
                  <view className='pd10'>
                    <text className='xxl major font-weight pr10'>{{ count.todo }}</text>
                    <text className='lg weak'>个</text>
                  </view>
                </view>
              </view>
              <view className='col-5 text-center'>
                <image className='iconSize' :src="todo"/>
              </view>
            </view>
          </view>
        </view>
        <view v-if="flag.mail === 1" className='col-6'>
          <view className='pr10 pt20' @click="goview('mail')">
            <view className='row row__align--center bgWhite card shadow-lg'>
              <view className='col-7'>
                <view className='pd20'>
                  <view className='pd10'>
                    <text className='lg font-weight'>爱情邮箱</text>
                  </view>
                  <view className='pd10'>
                    <text className='xxl major font-weight pr10'>{{ count.mail }}</text>
                    <text className='lg weak'>封</text>
                  </view>
                </view>
              </view>
              <view className='col-5 text-center'>
                <image className='iconSize' :src="mail"/>
              </view>
            </view>
          </view>
        </view>
        <view v-if="flag.photo === 1" className='col-6'>
          <view className='pl10 pt20' @click="goview('photo')">
            <view className='row row__align--center bgWhite card shadow-lg'>
              <view className='col-7'>
                <view className='pd20'>
                  <view className='pd10'>
                    <text className='lg font-weight'>共享相册</text>
                  </view>
                  <view className='pd10'>
                    <text className='xxl major font-weight pr10'>{{ count.photo }}</text>
                    <text className='lg weak'>张</text>
                  </view>
                </view>
              </view>
              <view className='col-5 text-center'>
                <image className='iconSize' :src="photo"/>
              </view>
            </view>
          </view>
        </view>
        <view v-if="flag.travel === 1" className='col-6'>
          <view className='pr10 pt20' @click="goview('travel')">
            <view className='row row__align--center bgWhite card shadow-lg'>
              <view className='col-7'>
                <view className='pd20'>
                  <view className='pd10'>
                    <text className='lg font-weight'>旅游足迹</text>
                  </view>
                  <view className='pd10'>
                    <text className='xxl major font-weight pr10'>{{ count.travel }}</text>
                    <text className='lg weak'>个</text>
                  </view>
                </view>
              </view>
              <view className='col-5 text-center'>
                <image className='iconSize' :src="travel"/>
              </view>
            </view>
          </view>
        </view>
      </view>
    </view>
  </view>
</template>

<script setup lang="ts">
import { ref } from 'vue';
import date from '../../static/imgs/svg/date.svg';
import todo from '../../static/imgs/svg/todo.svg';
import mail from '../../static/imgs/svg/mail.svg';
import photo from '../../static/imgs/svg/photo.svg';
import travel from '../../static/imgs/svg/travel.svg';
import wave from '../../static/imgs/user/wave.gif'
import { PAGE } from '../../utils/constant';
const state = {
  isBind:true,
  together:'365',
  count: {
    remember: 1,
    todo: 1,
    mail: 1,
    photo: 1,
    travel: 1
  },
  flag:{
    mail: 1,
    photo: 1,
    travel: 1
  },
};

const { isBind,together,count,flag } = state;

const user = {
  avatarUrl: '#',
  nickName: 'qlz'
}

const bindUser = {
  avatarUrl: '#',
  nickName: 'xhx'
}
const goview = (type: string) => {
  switch(type) {
    case 'mail':
      uni.navigateTo({
        url: `/pages/mail/mail`,
      });
      break;
    case 'remember':
      uni.navigateTo({
        url: '/pages/remember/remember',
      });
      break;
    case 'photo':
      uni.navigateTo({
        url: '/pages/photo/photo',
      });
      break;
    case 'todo':
      uni.navigateTo({
        url: '/pages/todo/todo',
      });
      break;
    case 'travel':
      /* uni.navigateTo({
        url: '/pages/todo/todo',
      }); */
      uni.showToast({
        title: '功能开发中'
      })
      break;
  }
};

const getCount = () => {
  count = {
    remember: 1,
    todo: 1,
    mail: 1,
    photo: 1,
    travel: 1
  }
}


</script>

<style lang="scss">
@import '@/static/css/mixn.scss';

page {
  background: $color-ec;
}
.iconSize {
  width: 110px;
  height: 110px;
}

.gif-wave {
  position: absolute;
  width: 100%;
  bottom: 0px;
  left: 0px;
  z-index: 99;
  mix-blend-mode: screen;
  height: 100px;
}
.image {
  width: 32Px;
}

.order{
  height: 20px;
  border-bottom-left-radius: 15px;
  border-bottom-right-radius: 15px;
  box-shadow:0 0 10px rgba(0, 0, 0, 0.1);
}


</style>