<template>
	<div class="SearchCard">
		<SearchCard
		v-for="card of cards" :key="card.id"
		v-bind:card="card" 
		/>
	</div>
</template>
<script type="text/javascript">
	import SearchCard from '@/components/SearchCard'
	export default {
		props: ['cards'], 
		components: {
			SearchCard
		}
	}
</script>
<style type="text/css" scoped>
.SearchCard{
	display: flex;
	flex-direction: row;
	justify-content: space-around;
	flex-wrap: wrap;
}
</style>