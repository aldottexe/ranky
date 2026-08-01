<script lang="ts">
    let { label, onClick = () => {} } : { label: string; onClick?: () => void } = $props();
</script>
<button 
    onclick={onClick}
    class="rounded-md px-2 py-4 bg-g2 block w-full hover:bg-a1 hover:text-g0 transition-colors duration-100 uppercase"
>
    {label}
</button>