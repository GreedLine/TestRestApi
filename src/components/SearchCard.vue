<template>
	<div class="card" v-bind:class="{favorite: card.favorite}">
		<div class="title">Название фильма: <br>{{card.name}}</div>
		<div class="year">Год начала проката: <br>{{card.year}}</div>
		<button v-on:click="card.favorite = !card.favorite">Избранное</button>
		{{card.favorite}}
	</div>

</template>

<style type="text/css" scoped>
.card{
	display: flex;
	flex-direction: column;
	justify-content: space-between;
	align-items: center;
	min-width: 200px;
	border: 1px solid black;
	border-radius: 5px;
	transition: .5s;
	line-height: 2em;
	padding: 10px;
	margin: 10px;
}
.title{
	height: 65px;
	margin-top: 5px;
}
button{
	margin: 10px 0px 10px 0px;
	width: 100px;
	height: 30px
}
.favorite{
	background: #FFBE40;
}
</style>

<script type="text/javascript">
	export default{
		props: ['card']
	}
</script>