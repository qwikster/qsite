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

<style>
    .images {
        display: grid;
        grid-template-columns: repeat(auto-fill, 88px);
        grid-auto-rows: 31px;
        padding: var(--pad-ui);
        justify-content: center;
        gap: var(--pad-ui)
    }
</style>
