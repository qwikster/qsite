<script>
    import { onMount } from "svelte";
    let images = $state([])
    let tiles = $state([])

    onMount(async () => {
      try {
        const response = await fetch('/88x31s.json');
        images = await response.json()
        tiles = shuffle(images)
      } catch (error) {
        console.error("Failed to load 88x31s:", error)
      }
    });

    function shuffle(array) {
      let shuffled = [...array];
      for (let i = shuffled.length - 1; i > 0; i--) {
     	const j = Math.floor(Math.random() * (i + 1));
     	[shuffled[i], shuffled[j]] = [shuffled[j], shuffled[i]];
      }
      return shuffled;
    }

    let copied = false
    function copy() {

    }

</script>

<div class="content">
    <div class="me">
        <!-- svelte-ignore a11y_missing_attribute -->
        <a href="https://qwik.top" title="now with 27% more doid per doid!" target="_blank"><img src="/88x31s/qwik.top.png"></a>
        <div>
            <span class="flavor">add my 88x31:</span>
            <button onclick={copy}>
                {copied ? "copied!" : "copy html"}
            </button>
        </div>
    </div>
    <div class="images">
        {#await tiles}
            <div>loading...</div>
        {:then tiles}
            {#each tiles as tile}
                <div class="image">
                    <a href={tile.url} title={tile.alt} target="_blank"><img alt={tile.alt} src={tile.img}></a>
                </div>
            {/each}
        {/await}
    </div>
</div>

<style>
    .content {
        padding: var(--pad-ui);
        justify-content: center;
        display: flex;
        flex-direction: column;
    }

    .images {
        display: grid;
        grid-template-columns: repeat(auto-fill, 88px);
        grid-auto-rows: 31px;
        justify-content: center;
        gap: var(--pad-ui)
    }

    .me {
        display: flex;
        justify-content: center;
        gap: var(--pad-ui);
        align-self: center;
        margin-bottom: var(--pad-ui);
        padding-bottom: var(--pad-ui);
        border-bottom: 2px solid #FFF;
    }

    .flavor {
        border-bottom: var(--border-hr) solid var(--col-secondary);
        align-self: center;
        margin-right: 6px;
        margin-bottom: 2px;
        font-size: var(--font-tiny);
        color: var(--col-ok);
    }

    button {
        background-color: var(--bg-2);
        border: var(--border-small) solid var(--col-border);
        padding: 2px 4px;
        border-radius: var(--round-button);
        color: var(--col-accent);
        font-family: var(--ff-button);
        font-size: var(--font-tiny);
        transition: 0.2s ease all;
    }

    button:hover {
        background-color: var(--bg-hover);
        border-color: var(--col-hover);
    }
</style>
