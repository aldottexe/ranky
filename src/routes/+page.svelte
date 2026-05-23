<script lang="ts">
	import type { orderableList_T } from '$lib/orderableList.svelte';
	import OrderableList from '$lib/orderableList.svelte';
	import RankedItem from '$lib/rankedItem.svelte';

	const items: orderableList_T = [
		{ name: 'pep', id: 0 },
		{ name: 'hawaiian', id: 1 },
		{ name: 'buff', id: 2 }
	];
</script>

<OrderableList {items} />

<!-- <ul class=""> -->
<!-- 	{#each items as item, i} -->
<!-- 		<RankedItem name={item} {i} moveUp={() => {}} moveDown={() => {}} /> -->
<!-- 	{/each} -->
<!-- </ul> -->
