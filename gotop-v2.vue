<!-- 
  Create by wanlixin 2017-11-25 00:59:23
  【功能描述】：回到顶部, 箭头的样式是采用iviewUI里面iconfont，大家也可以自定义
   传参：{
    size: 30,  // 箭头的大小 默认为30
    allowColor: "#ccc", // 箭头的颜色
    allowType: '', // 箭头的样式可有以下几种   
    “arrow-up-b”、“chevron-up"、"ios-arrow-up"、"ios-arrow-thin-up"、"android-arrow-up"
    allowImg: '' // 自定义一个向上的箭头 类似一个img的src
    bgColor: "#000", // 矩形背景颜色
    speed: 10 // 回到顶部的速率 越小越快 默认为10 
  }
 -->
<template>
  <div class="gotop-box" 
    v-show="status"
    :style="style" 
    @click="gototop">
    <Icon v-if="!options.allowImg" :type="options.allowType" :size="options.size" :color="options.allowColor"></Icon>
  </div>
</template>
<script>

export default {
  props: {
    options: {
      type: Object,
      default: function () {
        return {
          size: 30,
          allowColor: "#ccc",
          allowType: "arrow-up-a",
          allowImg: "",
          bgColor: "#000",
          speed: 10
        }
      }
    }
  },
  data () {
    return {
      style: {
        width: `${this.options.size / 50}rem`,
        height: `${this.options.size / 50}rem`,
        background: this.options.allowImg ? `url(${this.options.allowImg}) 0% 0% / 100% 100%` : this.options.bgColor
      },
      status: false,
      scrollTop: 0,
      timer: null
    }
  },
  mounted () {
    let _t = this;
    window.onscroll = function () {
      _t.scrollTop = document.body.scrollTop ? document.body.scrollTop : document.documentElement && document.documentElement.scrollTop ? document.documentElement.scrollTop : null
      _t.status = _t.scrollTop && _t.scrollTop > 0;
    }
  },
  methods: {
    gototop () {
      let _t = this;
      _t.timer = setInterval(function(){
        _t.scrollTop -= 100
        if (_t.scrollTop < 100) {
          _t.scrollTop = 0;
          _t.status = false;
          clearInterval(_t.timer);
        }
        scrollTo(0, _t.scrollTop)
      }, this.options.speed)
    }
  },
  destroyed () {
    clearInterval(this.timer)
  }
}
</script>
<style lang="stylus" scoped>
.gotop-box
  position: fixed
  right: 30px
  bottom: 100px
  display flex
  justify-content center
  align-items center
  opacity .75
</style>
