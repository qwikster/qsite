<script>
    import Hi from "../lib/Hi.svelte";

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
        <!-- svelte-ignore a11y_no_noninteractive_element_interactions -->
        <!-- svelte-ignore a11y_click_events_have_key_events -->
        <div style="display: flex; align-items: center;">
            <img src="{source}" alt="logo!" width="64px" on:click={chlogo} style="cursor: pointer;">
            <span style="font-family: var(--ff-header); color: var(--accent)">󰜴</span>
        </div>
        <button class="projects">BLAG</button>
        <button class="projects">PROJECTS</button>
    </div>
    <div class="panel">
        <Hi/>
        <p style="text-align: left;">
            I can't take it any more. Among Us has singlehandedly ruined my life. The other day my teacher was teaching us Greek Mythology and he mentioned a pegasus and I immediately thought <i></i>'Pegasus? more like Mega Sus!!!!' and I've never wanted to kms more. I can't look at a vent without breaking down and fucking crying. I can't eat pasta without thinking 'IMPASTA??? THATS PRETTY SUS!!!!' Skit 4 by Kanye West. The lyrics ruined me. A Mongoose, or the 25th island of greece. The scientific name for pig. I can't fucking take it anymore.
        </p>
        <p></p>
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
        display: flex;
        align-items: center;
        justify-content: space-between;
        margin-bottom: var(--pad-ui);
    }

    .panel {
        border: var(--border-panel) solid var(--col-border);
        padding: var(--pad-ui);
        border-radius: var(--round-panel);
        background-color: var(--col-bg);
    }

    p {
        color: var(--col-body);
        font-family: var(--ff-body), monospace;
        font-size: var(--font-text);
        margin: 0px;
        padding: 2px;
        line-height: 1.3;
    }

</style>
