<template>
	<ul class="list">
		<li 
			class="item" 
			v-for="item in letters" 
			:key="item"
			:ref="item"
			@touchstart.prevent="handleTouchStart"
			@touchmove="handleTouchMove"
			@touchend="handleTouchEnd"
			@click="handleClickItem"
		>
			{{ item }}
		</li>
	</ul>
</template>

<script>
export default {
	name: 'CityAlphabet',
	props: {
		cities: Object
	},
	computed: {
		letters () {
			const letters = []
			for (let i in this.cities) {
				letters.push(i)
			}
			return letters
		}
	},
	data () {
		return {
			touchStatus: false,
			startY: 0
		}
	},
	updated () {
		this.startY = this.$refs['A'][0].offsetTop
	},
	methods: {
		handleClickItem (e) {
			this.$emit('change', e.target.innerHTML)
		},
		handleTouchStart () {
			this.touchStatus = true
		},
		handleTouchMove (e) {
			if(this.touchStatus) {

				const touchY = e.touches[0].clientY - 80
				const index = Math.floor((touchY - this.startY) / 20)
				if( index >= 0 && index < this.letters.length) {
					this.$emit('change', this.letters[index])
				}
			}
		},
		handleTouchEnd () {
			this.touchStatus = false
		}
	}
}
</script>

<style lang="stylus" scoped>
	@import '~styles/varibles.styl'
	.list
		display: flex
		flex-direction: column
		justify-content: center
		position: absolute
		top: 1.6rem
		right: 0
		bottom: 0
		width: .4rem
		.item
			line-height: .4rem
			text-align: center
			color: $bgColor
</style>