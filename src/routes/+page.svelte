<script lang="ts">
	import ButtonLG from "$lib/ui/buttonLG.svelte";
	const {data} = $props()
	function pingRooms() {
		data.supabase.from("rooms").select("*").then((res) => {
		if (res.error) console.error(res.error)
		console.log(res)
	})	
	}
	function pingPlayers() {
		data.supabase.from("players").select("*").then((res) => {
		if (res.error) console.error(res.error)
		console.log(res)
	})	
	}

	function createRoom() {
		data.supabase.rpc("create_room", {player_name: "testy "+Math.floor(Math.random()*100), player_color: 0, room_name: "test_room "+Math.floor(Math.random()*100), room_max_entries: 1}).then((res) => {
			if (res.error) console.error(res.error)
			console.log(res);
		})
	}
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
		<ButtonLG label="create" onClick={createRoom} />
	</div>
	<ButtonLG label="ping room" onClick={pingRooms} />
	<ButtonLG label="ping players" onClick={pingPlayers} />
</div>