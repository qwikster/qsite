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
</script>

<div class="content">
    <div class="me">
        <div class="flavor">use mine!</div>
        <!-- svelte-ignore a11y_missing_attribute -->
        <div class="logobar">
            <span class="arrows">󰜴</span>
            <div>
                <a class="logo" href="https://qwik.top" title="now with 27% more doid per doid!" target="_blank"><img src="/88x31s/qwik.top.png"></a>
            </div>
            <span class="arrows">󰜱</span>
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
        flex-direction: column;
        justify-content: center;
        align-self: center;
        margin-bottom: 2px;
    }

    .flavor {
        font-family: var(--ff-info);
        margin-bottom: 2px;
        font-size: var(--font-tiny);
        color: var(--col-ok);
        align-self: center;
    }

    .logo {
        align-self: center;
    }

    .logobar {
        display: flex;
        align-items: center;
        justify-content: center;
        gap: var(--pad-ui);
    }

    .arrows {
        font-family: var(--ff-header);
        font-size: var(--font-header);
        color: var(--col-accent);
        padding-bottom: 6px;
    }
</style>
