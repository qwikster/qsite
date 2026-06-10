<script>
  import { onMount } from "svelte";
  let id = "loading"
  let date = "loading"
  let error = ""

  onMount(async () => {
    try {
      const response = await fetch(
        `https://api.github.com/repos/qwikster/qsite/commits`,
        {headers: {"Accept": "application/vnd.github+json"}}
      );
      if (!response.ok) throw new Error(`failed to fetch GitHub info: ${response.statusText}`)
      const data = await response.json();

      if (data && data.length > 0) {
        id = data[0].sha.substring(0, 7);
        date = new Date(data[0].commit.author.date).toLocaleTimeString()  + " " + new Date(data[0].commit.author.date).toLocaleDateString()
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
        <b style="color: var(--col-body);">{id}</b> at
        <b style="color: var(--col-body);">{date}</b> on
        <b><a target="_blank" href="https://github.com/qwikster/qsite">qwikster/qsite</a></b>
    </p>
{/if}

<style>
    p {
        color: var(--col-dim);
        font-family: var(--ff-body), monospace;
        font-size: var(--font-info);
        margin: 0px;
        padding: 2px;
        line-height: 1.3;
        text-align: center;
    }

    a {
        color: var(--col-hover);
    }
</style>
