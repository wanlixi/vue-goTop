<!-- 
【功能描述】：回到顶部
 -->
<template>
  <div class="gotop-box"><div class="gotop" @click="gototop"></div></div>
</template>
<script type="text/babel">
import $ from 'jquery'
export default {
  mounted () {
    $(window).on('scroll', function(){
      if ($(this).scrollTop() > 0) {
        $('.gotop').fadeIn()
      } else {
        $('.gotop').fadeOut()
      }
    })
  },
  methods: {
    gototop () {
      $('body,html').animate({ scrollTop: 0 }, 800)
    }
  }
}
</script>
<style lang="stylus" scoped>
.gotop-box
  position: fixed
  right: 30px
  bottom: 100px
  .gotop
    display: none
    background: url('~assets/img/common/gototop.png') no-repeat
    width: 51px
    height: 40px
    cursor: pointer
</style>
