<template>
  <div class="wrapper">
    <!--通过if判断来解决轮播第四张图为默认的bug,当props获取到了list的全部数据之后在创建swiper就不会有这个bug了,
    showSwiper本来是判断的条件，但是为了避免vue的逻辑性文件出现在模板语法厘米，所以把条件写在了计算属性里-->
  <swiper :options="swiperOption" v-if="showSwiper">
    <!-- slides -->
    <swiper-slide v-for="item of list" :key="item.id">
      <img class="swiper-img" :src="item.imgUrl"/>
    </swiper-slide>
    <!-- Optional controls -->
    <div class="swiper-pagination"  slot="pagination"></div>
    <!--<div class="swiper-button-prev" slot="button-prev"></div>-->
    <!--<div class="swiper-button-next" slot="button-next"></div>-->
    <!--<div class="swiper-scrollbar"   slot="scrollbar"></div>-->
  </swiper>
  </div>
</template>

<script>
export default {
  name: 'HomeSwiper',
  props: {
    list: Array
  },
  data () {
    return {
      swiperOption: {
        pagination: '.swiper-pagination',
        loop: true,
        autoplay: 1500,
        autoplayDisableOnInteraction: false
      }
    }
  },
  computed: {
    showSwiper () {
      return this.list.length
    }
  }
}
</script>

<style lang="stylus" scoped>
  .wrapper>>> .swiper-pagination-bullet-active
    background: #fff
  .wrapper
    width:100%
    height:0
    overflow:hidden
    padding-bottom: 27.85%
    .swiper-img
      width:100%
     margin-bottom: .4rem
</style>
