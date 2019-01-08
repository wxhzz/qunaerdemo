<template>
	<div class="icons">
		<swiper  :options="swiperOption">
			<swiper-slide  v-for="(page, index) in pages" :key="index">
				<div class="icon" v-for="item in page" :key="item.id">
					<img :src="item.imgUrl" class="icon-img">
					<p class="icon-content">{{ item.desc }}</p>
				</div>
			</swiper-slide>
			<div class="swiper-pagination"  slot="pagination"></div>
		</swiper>
	</div>
</template>

<script>
	export default {
		name: 'HomeIcons',
		props: {
			list: Array
		},
		data: function() {
			return {
				swiperOption: {
					autoplay: false,
					pagination: '.swiper-pagination'
				}
			}
		},
		computed: {
			pages: function() {
				const pages = []
				this.list.forEach((item, index) => {
					const page = Math.floor(index / 8)
					if(!pages[page]) {
						pages[page] = []
					}
					pages[page].push(item)
				})
				return pages
			}
		}
	}
</script>

<style lang="stylus" scoped>
	@import '~styles/mixins.styl'
	@import '~styles/varibles.styl'
	.icons >>> .swiper-container
		height: 0
		padding-bottom: 53.73%
	.icons >>> .swiper-pagination-bullet-active
		background: $slideBgColor
	.icon
		position: relative
		overflow: hidden
		float: left
		width: 25%
		height: 0
		padding-bottom: 25%
		.icon-img
			width: 1.1rem
			height: 1.1rem
			display: block
			position: absolute
			top: 0
			right: 0
			left: 0
			bottom: 0
			margin: .2rem auto
		.icon-content
			color: #212121
			height: .32rem
			line-height: .32rem
			font-size: .28rem
			text-align: center
			position: absolute
			right: 0
			left: 0
			bottom: .2rem
			ellipsis()
</style>
