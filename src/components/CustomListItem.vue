<template>
	<b-list-group-item
		:variant="(item.status === 'complete') ? 'success' : 'warning'"
		@click.left.ctrl="$emit('switch-status', item)"
	>
		{{item.text}}
		<b-badge
			variant="danger"
			size="sm"
			v-if="item.status !== 'complete'" 
			@click.left.exact="$emit('remove', item.id)"
		>
			X
		</b-badge>
	</b-list-group-item>
</template>

<script>
export default {
	name: 'CustomListItem',
	props: {
		item: Object
	}
}
</script>

<style scoped>
.list-group-item {
	transition: all 1s;
}
.list-group-item > .badge {
	cursor: pointer;
}
</style>
