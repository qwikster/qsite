<script>
    import Hi from "../lib/Hi.svelte";
    import Skills from "../lib/Skills.svelte";

    let kikuri = false;
    const logo1 = "/favicon.png";
    const logo2 = "/kikuri.png";

    $: source = kikuri ? logo2 : logo1
    function chlogo() {
      kikuri = !kikuri
    }
</script>

<div class="content">
    <div class="header">
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
    </div>
    <div class="panel">
        <Hi/>
        <p style="text-align: left;">
            Trying to be able to passably do as many useful things as possible, and
            is currently at least okay at a decent number!
            Passionate about supporting and creating hardware or software that works
            for you, not to raise a company's net worth.
        </p>
        <Skills/>


        <p>my hands are typing words long words that will take up space wooords</p>
    </div>
</div>

<style>
    .content {
        max-width: 640px;
        margin-bottom: 30vh;
        margin-left: 20px;
        margin-right: 20px;
        margin-top: 20px;
    }

    .header {
        display: grid;
        grid-template-columns: auto 1fr auto 1fr auto;
        align-items: center;
        margin-bottom: var(--pad-ui);
        padding: 0px 8vw;
    }

    .panel {
        border: var(--border-panel) solid var(--col-border);
        padding: var(--pad-ui);
        border-radius: var(--round-panel);
        background-color: var(--bg-1);
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

    p {
        color: var(--col-body);
        font-family: var(--ff-body), monospace;
        font-size: var(--font-text);
        margin: 0px;
        padding: 2px;
        line-height: 1.3;
    }

    hr {
        flex: 1;
        margin: 10px;
        border-color: var(--col-secondary)
    }
</style>
