<script lang="ts">
	import ButtonLG from "$lib/ui/buttonLG.svelte";

</script>
<div class="flex items-center justify-end h-screen flex-col max-w-100 mx-auto gap-10 pb-10">
	<div>
	<img src="/logo.svg" alt="logo" class="w-30 mb-3" />
	<p>
		Welcome to Polka, your simple group decision maker. Create or join a room below to start.
	</p>
	</div>

	<div class="flex w-full gap-2">
		<ButtonLG label="join" onClick={() => {}} />
		<ButtonLG label="create" onClick={() => {}} />
	</div>
</div>