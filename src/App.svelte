<script>
    import logo from "/favicon.png"
    import flag_ca from "/ca.svg"

    import Hi from "./lib/Hi.svelte";
</script>

<div class="content">
    <div class="header">
        <h1>coolass logo here</h1>
    </div>
    <div class="panel">
        <Hi/>
        <p style="text-align: left;">
            grrrr jappan 🇯🇵 is best country in teh world (sekai) !!!!🤬😡!!!👹🤬!!!!! west bAd grrrgghhhg japenis culture⛩🎎🎏 better than amrican🗽🍔👎!!! (&gt;~&lt;) vendor machine eveywhere 🗼and sakura trees are so 🌸 a e s t h e t i c 🌸 UwU if u hate it then your NOT a man of culture so shinē!!! ~hmph baka -_- 🏮
        </p>
    </div>
</div>

<style>
    .content {
        max-width: 900px;
        margin-bottom: 30vh;
        margin-left: 20px;
        margin-right: 20px;
        margin-top: 20px;
    }

    .header {
        display: flex;
        align-items: center;
        justify-content: center;
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

    h1 {
        color: var(--col-header);
        font-family: var(--ff-header), monospace;
        font-size: var(--font-header);
        margin: 0px;
    }
</style>
