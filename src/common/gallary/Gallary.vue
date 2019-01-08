<template>
	<div class="container" @click="handleHideGallary">
		<div class="wrapper">
	    <swiper :options="swiperOptions">
	      <swiper-slide 
	      	v-for="(item, index) in imgs"
					:key="index"
	      >
	        <img class="gallary-img" :src="item">
	      </swiper-slide>
	      <div class="swiper-pagination"  slot="pagination"></div>
	    </swiper>
		</div>
	</div>
</template>

<script>
export default {
	name: 'CommonGallary',
	props: {
		imgs: {
			type: Array,
			default () {
				return []
			}
		}
	},
	data () {
		return {
			swiperOptions: {
				pagination: '.swiper-pagination',
				paginationType: 'fraction',
				observer:true,
				observeParents:true
			}
		}
	},
	methods: {
		handleHideGallary () {
			this.$emit('change')
		}
	}
}
</script>

<style lang="stylus" scoped>
	.container >>> .swiper-wrapper
	 display flex
	 align-items center
	.container
		display: flex
		flex-direction: column
		justify-content: center
		position: fixed
		top: 0
		right: 0
		bottom: 0
		left: 0
		background: #000
		z-index: 99
		.wrapper
			width: 100%
			// overflow: hidden
			// height: 0
			// padding-bottom: 100%
			.gallary-img
				width: 100%
			.swiper-pagination
				position: fixed
				left: 0
				right: 0
				bottom: .7rem
				color: #fff
</style>