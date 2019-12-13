<template>
  <view class="container">
    <view class="content">
      <view>定制初始值 value=4</view>
      <sx-rate :value="4" />
    </view>

    <view class="content">
      <view>绑定值 value.sync</view>
      <text>当前值: {{rateSync}}</text>
      <sx-rate :value.sync="rateSync" />
    </view>

    <view class="content">
      <view>定制数量 max</view>
      <sx-rate :max="8" />
      <sx-rate :max="3" />
    </view>

    <view class="content">
      <view>禁用 disabled</view>
      <sx-rate disabled />
    </view>

    <view class="content">
      <view>手指滑动动画 animation={{animation}}</view>
      <sx-rate :animation="animation" />
      <button :type="animation?'warn':'primary'" size="mini" @click="animation = !animation">{{animation ? '关闭' : '开启'}}动画</button>
    </view>

    <view class="content">
      <view>定制颜色</view>
      <sx-rate :default-color="color.default" :active-color="color.active" />
      <label class="flex-box">
        <text>默认颜色</text>
        <input class="input" type="color" v-model="color.default">
      </label>
      <label class="flex-box">
        <text>激活颜色</text>
        <input class="input" type="color" v-model="color.active">
      </label>
    </view>

    <view class="content">
      <view>定制大小</view>
      <sx-rate :font-size="fontSize" />
      <view class="flex-box">font-size: <input class="input" type="text" v-model="fontSize"></view>
      <view class="note">同css的font-size,默认值为 inherit</view>
    </view>

    <view class="content">
      <view>星星间距</view>
      <sx-rate :margin="margin" />
      <view class="flex-box">margin: <input class="input" type="text" v-model="margin"></view>
      <view class="note">可定制星星间距</view>
    </view>

    <view class="content">
      <view>监听变化 @change</view>
      <sx-rate @change="onChange" />
      <ul>
        <li v-for="(item,i) in changeLog" :key="i">变化了,新的值为{{item}}</li>
      </ul>
    </view>

    <view class="content">
      <view>自定义类名</view>
      <sx-rate container-class="my-rate-box" rate-class="my-rate" />
      <view class="note">可以通过额外的class来调整为自己想要的样式</view>
      <view class="note">container-class</view>
      <view class="note">容器样式没有scope问题</view>
      <view class="note">rate-class</view>
      <view class="note">指定星星的类名在h5中会受到style的scope属性限制, 可以使用 /deep/ 解决</view>
    </view>

  </view>
</template>

<script>
  import SxRate from '@/components/sx-rate'

  export default {
    components: {
      SxRate
    },
    data() {
      return {
        rateSync: 2,

        animation: true,

        color: {
          default: '#ccc',
          active: '#FFB700'
        },

        fontSize: 'inherit',

        margin: '10px',

        changeLog: []
      }
    },
    methods: {
      onChange(e){
        this.changeLog.push(e)
      }
    }
  }
</script>

<style scoped>
  .container{
    font-size: 40upx;
    line-height: 1.4;
  }
  .content{
    background: #f1f1f1;
    margin-top: 16px;
  }
  .content:last-child{
    margin-bottom: 60px;
  }
  .flex-box{
    display: flex;
    align-items: center;
  }
  .input{
    border: 1px solid #ddd;
  }
  .note{
    color: #bbb;
    font-size: 14px;
  }

  /*rate的容器不受scope限制*/
  .my-rate-box{
    justify-content: space-around;
  }

  /*rate的星星在h5中受scope限制*/
  .my-rate{
    animation: scale .2s linear infinite;
  }
  /deep/ .my-rate{
    animation: rotate 2s linear infinite;
  }

  @keyframes rotate {
    from {
      transform: rotate(0deg);
    }

    50%{
      transform: rotate(360deg);
    }

    to{
      transform: rotate(360deg);
    }
  }
</style>
