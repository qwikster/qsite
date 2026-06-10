<script>
  import { onMount } from "svelte";
  let id = "loading"
  let date = "loading"
  let error = ""


  onMount(async () => {
    try {
      const response = await fetch(
        `https://github.com/qwikster/qsite/commits?per_page=1`,
        {headers: {"Accept": "application/vnd.github+json"}}
      );
      if (!response.ok) throw new Error(`failed to fetch GitHub info: ${response.statusText}`)
      const data = await response.json();

      if (data && data.length > 0) {
        id = data[0].sha.substring(0, 7);
        date = new Date(data[0].commit.author.date).toLocaleString()
      }
    } catch (err) {
      error = err.message;
    }
  });
</script>


{#if error}
    <p class="error">{error}</p>
{:else}
    <p>
        on commit
        <b>{id}</b> at
        <b>{date}</b> on
        <b><a target="_blank" href="https://github.com/qwikster/qsite">qwikster/qsite</a></b>
    </p>
{/if}

<style>
    p {
        color: var(--col-dim);
        font-family: var(--ff-body), monospace;
        font-size: var(--font-text);
        margin: 0px;
        padding: 2px;
        line-height: 1.3;
        text-align: center;
    }

    a {
        color: var(--col-hover);
    }
</style>
