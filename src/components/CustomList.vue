<template>
	<div class="item-list container mt-2">
		<b-card
			class="text-center"
			:title="list.title"
		>
			<b-input-group prepend="Новый пункт">
				<b-form-input
					v-model.trim="list.newItemText"
					@keyup.native.enter="addItem"
				></b-form-input>
				<b-input-group-append>
					<b-btn
						variant="primary"
						@click.left="addItem"
					>
						+
					</b-btn>
				</b-input-group-append>
			</b-input-group>
			<b-list-group class="mt-2">
				<transition-group name="list-animation">
					<CustomListItem
						v-for="item in list.items"
						:key="item.id"
						:item="item"
						@switch-status="switchStatus"
						@remove="removeItem"
					></CustomListItem>
				</transition-group>
			</b-list-group>
		</b-card>
	</div>
</template>

<script>
import CustomListItem from './CustomListItem.vue'

export default {
	name: 'CustomList',
	created () {
		this.list.newItemId = this.list.items.length + 1;
	},
	components: {
		CustomListItem
	},
	props: {
		list: Object
	},
	methods: {
		addItem () {
			if (!this.list.newItemText) return

			this.list.items.push({
				id: this.list.newItemId++,
				text: this.list.newItemText,
				status: 'incomplete'
			})
			this.list.newItemText = ''
		},
		removeItem (itemId) {
			this.list.items = this.list.items.filter(item => {
				return item.id !== itemId
			})
		},
		switchStatus (item) {
			switch (item.status) {
				case 'incomplete':
					item.status = 'complete'
					break
				case 'complete':
					item.status = 'incomplete'
					break
			}
		}
	}
}
</script>

<style scoped>
.list-animation-enter, .list-animation-leave-to {
	opacity: 0;
	transform: translateX(30px);
}
.list-animation-leave-active {
	position: absolute;
	width: 100%;
}
</style>
