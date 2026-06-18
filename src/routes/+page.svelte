<script>
    import Etc from "../lib/Etc.svelte";
    import Folder from "../lib/Folder.svelte";
    import Header from "../lib/Header.svelte";
    import Hi from "../lib/Hi.svelte";
    import Links from "../lib/Links.svelte";
    import Skills from "../lib/Skills.svelte";
    import Tile88x31s from "../lib/Tile88x31s.svelte";
</script>

<div class="content">
    <Header/>
    <div class="panel">
        <Hi/>
        <p style="text-align: left;">
            Working on being able to passably do as many useful things as possible, and
            is currently at least okay at a decent number!
            I try to support and create projects that work
            for you, not to raise a company's net worth.
        </p>
        <Skills/>
        <Folder name="Links" open=true>
            <Links/>
        </Folder>
        <Folder name="88x31s">
            <Tile88x31s/>
        </Folder>
        <Folder name="etc" open=true>
            <Etc/>
        </Folder>
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

    .panel {
        border: var(--border-panel) solid var(--col-border);
        padding: var(--pad-ui);
        border-radius: var(--round-panel);
        background-color: var(--bg-1);
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
