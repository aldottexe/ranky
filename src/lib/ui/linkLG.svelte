<script lang="ts">
    let { label, href } : { label: string; href: string } = $props();
</script>
<a 
    href={href}
    class="rounded-md text-center px-2 py-4 bg-g2 block w-full hover:bg-a1 hover:text-g0 transition-colors duration-100 uppercase"
>
    {label}
</a>