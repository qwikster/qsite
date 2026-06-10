<script>
    let kikuri = false;
    const logo1 = "/favicon.png";
    const logo2 = "/kikuri.png";

    $: source = kikuri ? logo2 : logo1
    function chlogo() {
      kikuri = !kikuri
    }
</script>

<div class="header">
    <hr style="border-color: transparent;">
    <button class="button" title="(blog)">weblog</button>
    <hr>
    <div class="logo">
        <span class="arrows">󰜱</span>
        <!-- svelte-ignore a11y_no_noninteractive_element_interactions -->
        <!-- svelte-ignore a11y_click_events_have_key_events -->
        <img src="{source}" alt="logo!" width="64px" on:click={chlogo} style="cursor: pointer;">
        <span class="arrows">󰜴</span>
    </div>
    <hr>
    <button class="button" title="(projects)">things</button>
    <hr style="border-color: transparent;">
</div>

<style>
    .header {
        display: grid;
        grid-template-columns: 1fr auto 1fr auto 1fr auto 1fr;
        align-items: center;
        margin-bottom: var(--pad-ui);
    }

    .button {
        background-color: var(--bg-2);
        border: var(--border-small) solid var(--col-border);
        padding: 2px 4px;
        border-radius: var(--round-button);
        color: var(--col-accent);
        font-family: var(--ff-button);
        transition: 0.2s ease all;
    }

    .button:hover {
        background-color: var(--bg-hover);
        border-color: var(--col-hover);
    }

    .logo {
        display: flex;
        align-items: center;
    }

    .arrows {
        font-family: var(--ff-header);
        font-size: var(--font-header);
        color: var(--col-accent);
    }

    hr {
        flex: 1;
        margin: 10px;
        border-color: var(--col-secondary)
    }
</style>
