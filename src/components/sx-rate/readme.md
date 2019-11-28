### rate 

评分

#### **属性说明**

 属性名 | 类型 | 默认值 | 说明
 ---|---|---|---  
  value | Number | 3 | 星星值,支持.sync修饰符
  max | Number | 5 | 最大星星数量
  disabled | Boolean | false | 是否禁用
  animation | Boolean | true | 开启手指滑动时星星的的动画效果
  defaultColor | String | '#ccc' | 默认星星颜色,同css的color
  activeColor | String | '#FFB700' | 滑选后星星颜色,同css的color
  fontSize | String | 'inherit' | 星星大小,同css的fontSize
  margin | String | '' | 星星间距, 可以是 1em, 10px等(注意,不支持upx)
  --- | --- | --- | ---
  @change | EventHandle |  | 星星值变化时回调,event=value
  
 
#### Tips

使用的是阿里的iconfont,不是uni-icon

#### 平台差异

测试支持H5,微信小程序;

理论支持其他平台,未测试nvue,
