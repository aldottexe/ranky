<script lang="ts">
	import './layout.css';
	import favicon from '$lib/assets/favicon.svg';

	let { children } = $props();

	const header = 'Ranky';
</script>

<svelte:head><link rel="icon" href={favicon} /></svelte:head>
<div class="m-5">
	<h1 class="m-5 flex text-4xl font-bold text-mauve-700">
		{#each header as l}
			<span class="block" style:rotate="{Math.round(Math.random() * 45) - 22.5}deg">{l}</span>
		{/each}
	</h1>
	{@render children()}
</div>
