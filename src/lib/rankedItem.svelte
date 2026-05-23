<script lang="ts">
	interface p {
		name: string;
		i: number;
		moveUp: () => void;
		moveDown: () => void;
	}
	const { name, i, moveUp, moveDown }: p = $props();

	const colors = ['text-emerald-600', 'text-orange-600', 'text-yellow-600'];
	const color = colors[i % colors.length];
</script>

<div class="my-2 flex rounded-xl bg-mauve-300 px-5 py-3 {color}" style:rotate={'-2deg'}>
	<h3 class="w-full capitalize">{name}</h3>
	<div class="flex gap-5">
		<button>^</button>
		<button>v</button>
	</div>
</div>
