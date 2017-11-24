# vue-goTop
基于vuejs开发的回到顶部组件，只要当前页面有向下滚动的高度，就会出现回到顶部的按钮，反之则隐藏

效果如下：
![](https://github.com/wanlixi/vue-goTop/blob/master/gotopv2.gif)

====================================2017-11-24========================================
移除了Jquery的依赖，并添加一些简单的动画效果
### 在父组件中可以这样使用
```
<template>
  <div class="parent">
    <go-top :options="{ allowImg, size }"></go-top>
    <!-- 默认样式 -->
    <!-- <go-top></go-top> -->
  </div>
</template>
import goTop from '@/compontens/gotop'
<script>
export default {
  compontents: { goTop },
  data () {
    return {
      allowImg: require('../../assets/img/common/allowImg.png'),
      size: 40
    }
  }
}
</script>

```
当然如果你不传箭头的图片，内部使用了iviewUI里面提供的5种iconfont箭头样式供你参考
传参：
```
{
    size: 30,  // 箭头的大小 默认为30
    allowColor: "#ccc", // 箭头的颜色
    allowType: '', // 箭头的样式可有以下几种   
    “arrow-up-b”、“chevron-up"、"ios-arrow-up"、"ios-arrow-thin-up"、"android-arrow-up"
    allowImg: '' // 自定义一个向上的箭头 类似一个img的src
    bgColor: "#000", // 矩形背景颜色
    speed: 10 // 回到顶部的速率 越小越快 默认为10
}
```
# 如果您喜欢的话，欢迎Star，Issues
