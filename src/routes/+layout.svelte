<script lang="ts">
  import "../app.css";
  import { invalidate } from '$app/navigation'
  import { onMount } from 'svelte'

  let { data, children } = $props()
  let { supabase, session } = $derived(data)

  onMount(() => {
    const { data: sub } = supabase.auth.onAuthStateChange((_event, newSession) => {
      if (newSession?.expires_at !== session?.expires_at) {
        invalidate('supabase:auth')
      }
    })
    return () => sub.subscription.unsubscribe()
  })
</script>

<div class="fixed p-3">
  {#if session}
    <p class="text-green-800">logged in</p>
    <button onclick={()=>{supabase.auth.signOut()}}> end session </button>
  {:else}
    <p class="text-red-800">logged out</p>
  {/if}
</div>

{@render children()}