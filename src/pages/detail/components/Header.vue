<template>
	<div>
		<router-link 
			tag="div" 
			class="header-back" 
			to="/"
			v-show="showBack"
		>
			<i class="iconfont back-icon">&#xe624;</i>
		</router-link>
		<div class="header-fixed" v-show="watchShowBack" :style="opacityStyle">
				景点详情
				<router-link to="/">
					<i class="iconfont back-city">&#xe624;</i>
				</router-link>
		</div>
	</div>
</template>

<script>
export default {
	name: 'DetailHeader',
	data () {
		return {
			showBack: true,
			opacityStyle: {
				opacity: 0
			}
		}
	},
	computed: {
		watchShowBack () {
			return !this.showBack
		}
	},
	methods: {
		handleScroll () {
			let scrollTop = document.documentElement.scrollTop
			console.log(scrollTop)
			if (scrollTop > 10) {
				let opacity = scrollTop / 130
				opacity = opacity > 1 ? 1 : opacity
				this.opacityStyle = {
					opacity: opacity
				}
				this.showBack = false
			}else {
				this.showBack = true
			}
		}
	},
	activated () {
		window.addEventListener('scroll', this.handleScroll)
	}
	// deactivated () {
	// 	window.removeEventListener('scroll', this.handleScroll)
	// }
}
</script>

<style lang="stylus" scoped>
	@import '~styles/varibles.styl'
	.header-back
		position: absolute
		top: .2rem
		left: .2rem
		width: .72rem
		height: .72rem
		border-radius: .36rem
		background: #65646a
		.back-icon
			color: #fff
			font-size: .36rem
			line-height: .72rem
			margin-left: .18rem
	.header-fixed
		position: fixed
		top: 0
		left: 0
		width: 100%
		height: .88rem
		line-height: .88rem
		text-align: center
		font-size: .32rem
		background: $bgColor
		color: #fff
		z-index: 2
		.back-city
			position: absolute
			top: 0
			left: 0
			width: 0.88rem
			font-size: .36rem
			text-align: center
			color: #fff
</style>