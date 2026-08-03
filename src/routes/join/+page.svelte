<script>
	import Arrowcta from "$lib/ui/arrowcta.svelte";
	import Field from "$lib/ui/field.svelte";

</script>
<div class="flex flex-col gap-2 w-full">
<Field title="name" placeholder="adog" id="namefield" value=""/>
<Field title="room" placeholder="adog" id="roomfield" value=""/>
</div>
<Arrowcta label="join" href="/join" active={true}/>