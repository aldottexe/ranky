<script lang="ts">
	import { flip } from 'svelte/animate';

	export type orderableItem_T = { name: string; id: number };
	export type orderableList_T = orderableItem_T[];

	let { items = $bindable<orderableList_T>([]) }: { items: orderableList_T } = $props();

	let currentDragged: number | null = null;
	let draggedOver: number | null = null;

	// handle colors
	const colors = ["bg-a1", "bg-a2", "bg-a3", "bg-a4", "bg-a5", "bg-a6", "bg-a7"];
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

<div class="flex">
	<ol>
		{#each items as _, i (i)}
			<li class="my-2 flex justify-center rounded-3xl px-5 py-5 [user-drag:none] text-g5 max-w-min">
				{i + 1}.
			</li>
		{/each}
	</ol>
	<ul class="w-full max-w-80">
	{#each items as li, i (li.id)}
		<li
			draggable="true"
			ondragstart={(e) => onDragStart(e, i)}
			ondragover={(e) => onDragOver(e, i)}
			ondragend={() => {
				currentDragged = null;
				draggedOver = null;
			}}
			class="my-2 flex justify-center rounded-3xl px-5 py-5 [user-drag:none] text-g0 {getColorFromID(li.id)}"
			animate:flip={{ duration: 300 }}
			style:rotate="{Math.round(Math.random() * 2) - 1}deg"
		>
			{li.name}
		</li>
	{/each}
</ul>
</div>
