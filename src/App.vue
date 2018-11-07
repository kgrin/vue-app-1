<template>
	<div id="app">
		<h1 v-html="header"></h1>
		<hr>
		<CustomList
			v-for="list in lists"
			:key="list.id"
			:list="list"
		/>
		<hr>
		<h3 v-html="footer"></h3>
	</div>
</template>

<script>
import CustomList from './components/CustomList.vue'

export default {
	name: 'app',
	components: {
		CustomList
	},
	data () {
		return {
			header: 'Моё первое приложение на Vue.js + vue-bootstrap',
			footer: `<ul>
				<li>LClick по кнопке "+" или нажатие клавиши Enter в поле для ввода добавляет новый элемент в список</li>
				<li>Переключение статуса пункта списка с помощью сочетания Ctrl + LClick</li>
				<li>Удаление пункта списка с помощью LClick по кнопке "X"</li>
			<ul>`,
			lists: [
				{
					id: 1,
					title: 'Список дел',
					newItemId: 0,
					newItemText: '',
					items: [
						{
							id: 1,
							text: 'Выбрать фреймворк для изучения',
							status: 'complete'
						},
						{
							id: 2,
							text: 'Попрактиковаться с Vue.js',
							status: 'incomplete'
						},
						{
							id: 3,
							text: 'Лечь спать в 22:00',
							status: 'incomplete'
						}
					]
				}, {
					id: 2,
					title: 'Список покупок',
					newItemId: 0,
					newItemText: '',
					items: [
						{
							id: 1,
							text: 'Соль',
							status: 'complete'
						},
						{
							id: 2,
							text: 'Молоко',
							status: 'incomplete'
						},
						{
							id: 3,
							text: 'Торт',
							status: 'complete'
						},
						{
							id: 4,
							text: 'Наушники',
							status: 'incomplete'
						}
					]
				}
			]
		}
	}
}
</script>

<style>
</style>
