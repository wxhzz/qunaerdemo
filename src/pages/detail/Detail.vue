<template>
	<div>
		<detail-banner 
			:sightName="sightName" 
			:bannerImg="bannerImg"
			:gallaryImgs="gallaryImgs"
		>
		</detail-banner>
		<detail-header></detail-header>
		<div class="content">
			<detail-list :categoryList="categoryList"></detail-list>
		</div>
	</div>
</template>

<script>
import DetailBanner from './components/Banner'
import DetailHeader from './components/Header'
import DetailList from './components/List'
import axios from 'axios'
export default {
	name: 'Detail',
	components: {
		DetailBanner,
		DetailHeader,
		DetailList
	},
	data () {
		return {
			sightName: '',
			bannerImg: '',
			gallaryImgs: [],
			categoryList: []
		}
	},
	methods: {
		getDetailInfo () {
			axios.get('/api/detail.json', {
				params: {
					id: this.$route.params.id
				}
			}).then(this.getDetailInfoSucc)
		},
		getDetailInfoSucc (res) {
			let data = res.data
			if (data.ret && data.data) {
				this.sightName = data.data.sightName
				this.bannerImg = data.data.bannerImg
				this.gallaryImgs = data.data.gallaryImgs
				this.categoryList = data.data.categoryList
			}
		}
	},
	mounted () {
		this.getDetailInfo()
	}
}
</script>

<style lang="stylus" scoped>
	.content
		height: 50rem
</style>