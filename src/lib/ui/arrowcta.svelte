<script lang="ts">
    let { label, href, active = true } : { label: string; href: string; active: boolean } = $props();
</script>
<a 
    href={href}
    class="rounded-md text-center px-2 py-4 {active ? 'bg-a2' : 'bg-g1'} block w-full hover:bg-a1 hover:text-g0 transition-colors duration-100 uppercase text-g0"
>
    {label}
</a>