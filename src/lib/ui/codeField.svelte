<script lang="ts">
    interface p {
        title: string
        value: string
        id: string
    }
    let {value = $bindable(""), title, id} : p = $props();

    function keyHandler(e: KeyboardEvent) {
        if (e.key === "Backspace") {
            value = value.slice(0, -1);
            //if key is a number, add it to the value string, but only if the value string is less than 6 characters long
        } else if (e.key.length === 1 && value.length < 6 && !isNaN(parseInt(e.key))) {
            value += e.key;
        }
    }

</script>
{#snippet codeHalf(code: string)}
<span class="block px-4 py-1 min-w-16 rounded-lg bg-g1 text-center">{code}</span>
{/snippet}

<div 
class="flex gap-2 relative w-full items-center"
onkeydown={keyHandler} 
role="textbox"
tabindex="0"
>
    <label 
    for={id} 
    class="block bg-g2 px-4 py-1 min-w-20 rounded-lg font-bold uppercase text-center relative"
    
    >{title}</label>
    <div class="flex" id={id}>
        {@render codeHalf(value.slice(0, 3))} 
        <span class="block min-w-5 py-1 text-center">-</span>
        {@render codeHalf(value.slice(3, 6))}
    </div>
</div>