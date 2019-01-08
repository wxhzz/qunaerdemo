<template>
	<div class="header">
		<div class="header-left">
			<i class="iconfont back-icon">&#xe624;</i>
		</div>
    <div class="header-input">
    	<i class="iconfont search-icon">&#xe632;</i>
    	输入城市/景点/游玩主题123
    </div>
    <router-link to="/city">
	    <div class="header-right">
				{{ this.city }}
	    	<i class="iconfont city-icon">&#xe601;</i>
	    </div>
    </router-link>
  </div>
</template>

<script>
import { mapState } from 'vuex'
export default {
  name: 'HomeHeader',
  computed: {
  	...mapState(['city'])
  }
}
</script>

<style lang="stylus" scoped>
	@import '~styles/varibles.styl'
	.header
		display: flex
		height: .88rem
		line-height: .88rem
		background: $bgColor
		.header-left
			width: .88rem
			float: left
			text-align: center
			color: #fff
			.back-icon
				font-size: .36rem
		.header-input
			flex: 1
			margin-top: .12rem
			margin-bottom: .12rem
			line-height: .64rem
			background: #fff
			border-radius: .08rem
			color: #e4e7ea
			.search-icon
				margin-left: .2rem
				font-size: 0.3rem
		.header-right
			min-width: 1.12rem
			padding: 0 .1rem
			float: right
			text-align: center
			color: #fff
			.city-icon
				font-size: 0.24rem
</style>
