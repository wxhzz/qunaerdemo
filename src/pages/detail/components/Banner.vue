<template>
	<div>
		<div class="banner" @click="handleShowGallary">
			<img class="banner-img" :src="this.bannerImg" >
			<div class="banner-info">
				<div class="banner-title">{{ this.sightName }}</div>
				<div class="banner-number">
					<i class="iconfont banner-icon">&#xeb05;</i>{{ this.gallaryImgs.length }}
				</div>
			</div>
		</div>
		<fade-animation>
			<common-gallary 
				:imgs="this.gallaryImgs" 
				v-show="showGallary"
				@change="handleHideGallary"
			></common-gallary>	
		</fade-animation>
	</div>
</template>

<script>
import CommonGallary from 'common/gallary/Gallary'
import FadeAnimation from 'common/fade/FadeAnimation'
export default {
	name: 'DetailBanner',
	props: {
		sightName: String,
		bannerImg: String,
		gallaryImgs: Array
	},
	components: {
		CommonGallary,
		FadeAnimation
	},
	data () {
		return {
			showGallary: false
		}
	},
	methods: {
		handleShowGallary () {
			this.showGallary = true
		},
		handleHideGallary () {
			this.showGallary = false
		}
	}
}
</script>

<style lang="stylus" scoped>
	.banner
		overflow: hidden
		height: 0
		padding-bottom: 55%
		position: relative
		.banner-img
			width: 100%
		.banner-info
			display: flex
			position: absolute
			left: 0
			right: 0
			bottom: 0
			line-height: .6rem
			color: #fff
			background-image: linear-gradient(top, rgba(0, 0, 0, 0), rgba(0, 0, 0, .8))
			.banner-title
				flex: 1
				font-size: .32rem
				padding: 0 .3rem
				z-index: 1
			.banner-number
				margin-top: .14rem
				padding: 0 .4rem
				height: .32rem
				line-height: .32rem
				border-radius: .2rem
				background: rgba(0, 0, 0, .8)
				font-size: .24rem
				z-index: 1
				.banner-icon
					font-size: .28rem
					margin-right: .04rem
</style>