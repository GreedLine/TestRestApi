<template>
	<div class="CreateMain">
		<div class="Create">
			<h2>Создание новой карточки фильма</h2>	
			<form @submit.prevent ="onSubmit">
				<input type="text" name="name" v-model="name" placeholder="Введите название фильма..." >
				<input type="text" name="year" v-model="year" placeholder="Введите год выхода в прокат...">
				<button type="submit">Добавить!</button>
				{{name}}
			</form>
		</div>
	</div>
</template>


<script type="text/javascript">



	export default {
		data(){
			return{
				name: '',
				year: ''
			}
		},
		methods: {
			onSubmit() {
				if (this.name.trim()) {
					const newCard = {
						name: this.name,
						year: this.year,
						favorite: false
					}
					this.$emit('add-card', newCard)
				}	
			}
		}
	}
</script>
<style type="text/css" scoped>
.Create{
	padding-top: 15px;
}
.Create, form{
	display: flex;
	flex-direction: column;
	align-items: center;
}
form{
	display: flex;
	flex-direction: column;
}
input{
	box-sizing: border-box;
	min-width: 350px;
	padding: 5px;
	max-width: 350px;
	margin: 3px;
}
</style>