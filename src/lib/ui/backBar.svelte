<script lang="ts">
    const {name, backref="/"} : {name: string, backref?: string} = $props();
</script>
<div class="flex justify-between align-center uppercase px-2">
    <h2>{name}</h2>
    <a href={backref} class="hover:text-a1 transition-colors">
        BACK
    </a>
</div>