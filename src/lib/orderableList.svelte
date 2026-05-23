<script lang="ts">
	import { flip } from 'svelte/animate';

	export type orderableItem_T = { name: String; id: number };
	export type orderableList_T = orderableItem_T[];

	let { items = $bindable<orderableList_T>([]) }: { items: orderableList_T } = $props();

	let currentDragged: number | null = null;
	let draggedOver: number | null = null;

	// handle colors
	const colors = ['text-emerald-600', 'text-orange-600', 'text-yellow-600'];
	function getColorFromID(id: number) {
		return colors[id % colors.length];
	}

	function onDragOver(e: DragEvent, draggingOver: number) {
		e.preventDefault();
		if (currentDragged === null || draggingOver === currentDragged) return;
		const movingItem = items[currentDragged];
		items.splice(currentDragged, 1);
		items.splice(draggingOver, 0, movingItem);
		currentDragged = draggingOver;
		items = items;
	}

	function onDragStart(e: DragEvent, i: number) {
		// e.preventDefault();
		currentDragged = i;
		const ghost = new Image();
		ghost.src = 'data:image/gif;base64,R0lGODlhAQABAIAAAAAAAP///yH5BAEAAAAALAAAAAABAAEAAAIBRAA7';
		e.dataTransfer?.setDragImage(ghost, 0, 0);
	}

	$inspect(items);
</script>

<ul>
	{#each items as li, i (li.id)}
		<li
			draggable="true"
			ondragstart={(e) => onDragStart(e, i)}
			ondragover={(e) => onDragOver(e, i)}
			ondragend={() => {
				currentDragged = null;
				draggedOver = null;
			}}
			class="my-2 flex rounded-xl bg-mauve-300 px-5 py-3 [user-drag:none] {getColorFromID(li.id)}"
			animate:flip={{ duration: 300 }}
		>
			{li.name}
		</li>
	{/each}
</ul>
