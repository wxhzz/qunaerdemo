<template>
  <div class="wrapper">
    <swiper :options="swiperOption" v-if="showSwiper">
      <!-- slides -->
      <swiper-slide v-for="item in this.list" :key="item.id">
        <img class="swiper-image" :src="item.imgUrl">
      </swiper-slide>
      <!-- Optional controls -->
      <div class="swiper-pagination"  slot="pagination"></div>
    </swiper>
  </div>
</template>

<script>
	export default {
		name: 'HomeSwiper',
    props: {
      list: Array
    },
		data: function() {
			return {
        swiperOption: {
          autoplay: 2000,
          pagination: '.swiper-pagination',
          loop: true
        }
      }
		},
    computed: {
      showSwiper: function() {
        return this.list.length
      }
    }
	}
</script>

<style lang="stylus" scoped>
  .wrapper >>> .swiper-pagination-bullet-active
    background: #fff
  .wrapper
    overflow: hidden
    width: 100%
    height: 0
    padding-bottom: 26.67%
    .swiper-image
      width: 100%
</style>