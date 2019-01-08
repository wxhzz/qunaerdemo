<template>
	<div>
		<div class="title">周末去哪儿</div>
		<ul>
			<li class="item border-bottom" v-for="item in list" :key="item.id">
				<div class="item-img-wrapper">
					<img class="item-img" :src="item.imgUrl">
				</div>
				<div class="item-info">
					<p class="item-title">{{ item.title }}</p>
					<p class="item-desc">{{ item.desc }}</p>
				</div>
			</li>
		</ul>
	</div>
</template>

<script>
	export default {
		name: 'HomeWeekend',
		props: {
			list: Array
		}
	}
</script>

<style lang="stylus" scoped>
	@import '~styles/mixins.styl'
	.title
		line-height: .8rem
		text-indent: .2rem
		background: #f5f5f5
	.item-img-wrapper
		overflow: hidden
		height: 0
		padding-bottom: 37.09%
		.item-img
			width: 100%
	.item-info
		flex: 1
		padding: .2rem
		min-width: 0
		.item-title
			font-size: .28rem
			color: #212121
			padding: .08rem 0
			ellipsis()
		.item-desc
			font-size: .24rem
			color: #616161
			padding: .12rem 0
			ellipsis()
</style>