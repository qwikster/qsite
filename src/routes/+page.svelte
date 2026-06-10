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

        <div class="skills">
            <div class="skill-tier">
                <div class="skill-desc" style="color: var(--col-ok);">
                    <div class="skill-icon"></div>
                    <div class="skill-text">good at!</div>
                </div>
                <div class="skill-list">
                    <div class="skill-line" style="color: var(--bg-ok);">
                        <span class="skill">aaaa</span>
                        <span class="skill">aaaaaa</span>
                        <span class="skill">aaaaaaaaa</span>
                        <span class="skill">aaaaaaaa</span>
                        <span class="skill">aaaa</span>
                        <span class="skill">aaaaaaaaaaaaaa</span>
                        <span class="skill">aaaaaaaa</span>
                        <span class="skill">aaaaaaaaaaaaaaaaa</span>
                    </div>
                </div>
            </div>
            <div class="skill-tier">
                <div class="skill-desc" style="color: var(--col-meh);">
                    <div class="skill-icon"></div>
                    <div class="skill-text">learn as needed</div>
                </div>
                <div class="skill-list">
                    <div class="skill-line" style="color: var(--bg-meh);">
                        <span class="skill">jjjjjjjjjjjjjjjj</span>
                        <span class="skill">jjj</span>
                        <span class="skill">jjjjjjjjjjj</span>
                        <span class="skill">jjjjj</span>
                        <span class="skill">jjjjjjjjjjjjjjjjjjjjjjjjjjjjjjjj</span>
                        <span class="skill">jjjjjjjjjjjj</span>
                    </div>
                </div>
            </div>
            <div class="skill-tier">
                <div class="skill-desc" style="color: var(--col-wait);">
                    <div class="skill-icon"></div>
                    <div class="skill-text">still learning</div>
                </div>
                <div class="skill-list">
                    <div class="skill-line" style="color: var(--bg-wait);">
                        <span class="skill">eeeeee</span>
                        <span class="skill">eeeeeeeee</span>
                        <span class="skill">eeeeee</span>
                        <span class="skill">eeeeeeee</span>
                        <span class="skill">eeee</span>
                        <span class="skill">eeeeeeeeeee</span>
                        <span class="skill">eeeeee</span>
                        <span class="skill">eeeeeeeeeeeeeeeeeeee</span>
                    </div>
                </div>
            </div>
            <div class="skill-tier">
                <div class="skill-desc" style="color: var(--col-bad);">
                    <div class="skill-icon"></div>
                    <div class="skill-text">prefer not</div>
                </div>
                <div class="skill-list">
                    <div class="skill-line" style="color: var(--bg-bad);">
                        <span class="skill">ggggggg</span>
                        <span class="skill">ggggg</span>
                        <span class="skill">ggg</span>
                        <span class="skill">ggggg</span>
                        <span class="skill">ggggggg</span>
                        <span class="skill">gggg</span>
                    </div>
                </div>
            </div>

        </div>

        <p>my hands are typing words long words that will take up space wooords</p>
    </div>
</div>

<style>
    .skills {
        display: flex;
        flex-direction: column;
        margin: var(--pad-ui) 0px;
        gap: var(--pad-text);
    }

    .skill-tier {
        display: flex;
    }

    .skill-desc {
        display: flex;
        flex-direction: column;
        flex-shrink: 0;
        background-color: var(--bg-0);
        font-family: var(--ff-info);
        font-size: var(--font-small);
        border: 1px solid var(--bg-2);
        border-radius: var(--border-panel);
        padding: var(--pad-text);
        margin-right: var(--pad-ui);
        justify-content: center;
    }

    .skill {
        background-color: var(--bg-2);
        padding: var(--pad-tiny) var(--pad-text);
        border: 1px solid var(--bg-4);
        border-radius: var(--border-panel);
        font-family: var(--ff-info);
        font-size: var(--font-tiny);
        display: inline-block;
        margin-bottom: 1px;
    }

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
