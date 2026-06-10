<script>
    import Folder from "../lib/Folder.svelte";
    import Header from "../lib/Header.svelte";
    import Hi from "../lib/Hi.svelte";
    import Skills from "../lib/Skills.svelte";
</script>

<div class="content">
    <Header/>
    <div class="panel">
        <Hi/>
        <p style="text-align: left;">
            Working on being able to passably do as many useful things as possible, and
            is currently at least okay at a decent number!
            Passionate about supporting and creating hardware or software that works
            for you, not to raise a company's net worth.
        </p>
        <Skills/>
        <Folder name="Links">

        </Folder>
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
