<script lang="ts">
  let { data } = $props()
  let email = $state('')

  async function login() {
    const { data: d, error } = await data.supabase.auth.signInAnonymously()
    if (error) console.error(error);
    console.log(d);
  }
</script>

<input bind:value={email} type="email" />
<button onclick={login}>login</button>