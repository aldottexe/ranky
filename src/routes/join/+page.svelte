<script>
	import Arrowcta from "$lib/ui/arrowcta.svelte";
	import BackBar from "$lib/ui/backBar.svelte";
	import CodeField from "$lib/ui/codeField.svelte";
	import Field from "$lib/ui/field.svelte";

</script>
<div class="flex flex-col gap-2 w-full">
<BackBar name="join room"/>
<Field title="name" placeholder="adog" id="namefield" value=""/>
<Field title="room" placeholder="xxx-xxx" id="roomfield" value=""/>
<CodeField title="code" id="codefield" value=""/>
</div>
<Arrowcta label="join" href="/join" active={true}/>