<template>
	<div class="header">
		城市选择
		<router-link to="/">
			<i class="iconfont back-city">&#xe624;</i>
		</router-link>
	</div>
</template>

<script>
export default {
	name: 'CityHeader'
}
</script>

<style lang="stylus" scoped>
	@import '~styles/varibles.styl'
	.header
		position: relative
		overflow: hidden
		height: .88rem
		line-height: .88rem
		text-align: center
		font-size: .32rem
		background: $bgColor
		color: #fff
		.back-city
			position: absolute
			top: 0
			left: 0
			width: 0.88rem
			font-size: .36rem
			text-align: center
			color: #fff
</style>
