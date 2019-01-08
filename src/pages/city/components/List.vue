<template>
	<div class="list" ref="wrapper">
		<div>
			<div class="area">
				<div class="title border-topbottom" ref="city">当前城市</div>
				<div class="button-list">
					<div class="button-wrapper">
						<div class="button">{{ this.currentCity }}</div>
					</div>
				</div>
			</div>
			<div class="area">
				<div class="title border-topbottom">热门城市</div>
				<div class="button-list">
					<div 
						class="button-wrapper" 
						v-for="item in citylist" 
						:key="item.id"
						@click="handleItemClick(item.name)"
					>
						<div class="button">{{ item.name }}</div>
					</div>
				</div>
			</div>
			<div 
				class="area" 
				v-for="(item, key) in cities" 
				:key="key" 
				:ref="key"
			>
				<div 
					class="title border-topbottom"
				>
					{{ key }}
				</div>
				<div class="item-list">
					<div 
						class="item border-bottom"
						v-for="innerItem in item"
						:key="innerItem.id"
						@click="handleItemClick(innerItem.name)"
					>
						{{ innerItem.name }}
					</div>
				</div>
			</div>
		</div>
	</div>
</template>

<script>
import BScroll from 'better-scroll'
import { mapState } from 'vuex'
export default {
	name: 'CityList',
	props: {
		citylist: Array,
		cities: Object,
		letter: String
	},
	computed: {
		...mapState({
			currentCity: 'city'
		})
	},
	methods: {
		handleItemClick (city) {
			this.$store.commit('changeCity', city)
			this.$router.push('/')
		}
	},
	watch: {
		letter () {
			if(this.letter) {
				const element = this.$refs[this.letter][0]
				this.scroll.scrollToElement(element)
			}
		}
	},
	mounted() {
		this.scroll = new BScroll(this.$refs.wrapper)
		// console.log(this.$refs.wrapper)
	},
}
</script>

<style lang="stylus" scoped>
	.border-topbottom
		&:before
			border-color: #ccc
		&:after
			border-color: #ccc
	.border-bottom
		&:after
			border-color: #ccc
	.list
		overflow: hidden
		position: absolute
		top: 1.6rem
		right: 0
		bottom: 0
		left: 0
		.title
			line-height: .54rem
			background: #eee
			padding-left: .2rem
			color: #666
			font-size: .26rem
		.button-list
			overflow: hidden
			padding: .1rem .6rem .1rem .1rem
			.button-wrapper
				float: left
				width: 33.33%
				.button
					margin: .1rem
					padding: .1rem 0
					text-align: center
					border: .02rem solid #ccc
					border-radius: .06rem
		.item-list
			.item
				line-height: .76rem
				color: #666
				padding-left: .2rem
</style>