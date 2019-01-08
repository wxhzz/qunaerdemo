<template>
  <div id="app">
  	<keep-alive>
  	<!-- <keep-alive exclude="Detail">Detail页面Header失效 -->
    	<router-view/>
  	</keep-alive>
  </div>
</template>

<script>
export default {
  name: 'App'
}
</script>

<style>

</style>
