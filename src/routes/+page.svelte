<script>
    import Etc from "../lib/Etc.svelte";
    import Folder from "../lib/Folder.svelte";
    import Header from "../lib/Header.svelte";
    import Hi from "../lib/Hi.svelte";
    import Links from "../lib/Links.svelte";
    import Skills from "../lib/Skills.svelte";
    import Tile88x31s from "../lib/Tile88x31s.svelte";

    import { onMount } from "svelte";
    let images = $state([])
    let tools = $state([])

    onMount(async () => {
      try {
        const response = await fetch('/tools.json');
        images = await response.json()
        tools = shuffle(images)
      } catch (error) {
        console.error("Failed to load tools:", error)
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
        <Folder name="Links">
            <Links/>
        </Folder>
        <Folder name="88x31s">
            <Tile88x31s/>
        </Folder>
        <Folder name="etc">
            <Etc/>
        </Folder>
        <p class="footer"> icons and 88x31s all have hover text and links!</p>
        <div class="tools">
            <div class="track">
                {#await tools}
                    <span>loading tools...</span>
                {:then}
                    {#each tools as tool}
                        <div class="slide">
                            <a href={tool.url} title={tool.alt} target="_blank"><img width="40px" alt={tool.alt} src={tool.img}></a>
                        </div>
                    {/each}
                    <!-- infinite scroll -->
                    {#each tools as tool}
                        <div class="slide">
                            <a href={tool.url} title={tool.alt} target="_blank"><img width="40px"  alt={tool.alt} src={tool.img}></a>
                        </div>
                    {/each}
                {/await}
            </div>
        </div>
        <p class="footer" style="color: var(--col-dim);">Made with <span style="color: var(--flag-ca);"></span>, 2026 | Uses <a href="GPLv3.md" target="_blank">GPL v3.0</a></p>
    </div>
</div>

<style>
    .content {
        max-width: min(640px, 90vw);
        margin-bottom: 30vh;
        margin-left: 20px;
        margin-right: 20px;
        margin-top: 20px;
        width: calc(100% - 40px);
        min-width: 0;
    }

    .panel {
        border: var(--border-panel) solid var(--col-border);
        padding: var(--pad-ui);
        border-radius: var(--round-panel);
        background-color: var(--bg-1);
        min-width: 0;
    }

    p {
        color: var(--col-body);
        font-family: var(--ff-body), monospace;
        font-size: var(--font-text);
        margin: 0px;
        padding: 2px;
        line-height: 1.3;
    }

    .tools {
        overflow: clip;
        width: 100%;
        padding: var(--pad-ui) 0;
    }

    .track {
        display: flex;
        flex-wrap: nowrap;
        width: max-content;
        animation: scroll 30s linear infinite;
    }

    .track:hover { animation-play-state: paused; }

    .slide {
        width: 48px;
        box-sizing: border-box;
        flex: 0 0 48px;
    }

    .slide img {
        border-radius: var(--round-panel);
        display: block;
    }

    .footer {
        font-family: var(--ff-info);
        margin-bottom: 2px;
        font-size: var(--font-tiny);
        color: var(--col-ok);
        align-self: center;
        text-align: center;
    }

    a {
        color: var(--col-hover);
        transition: all 0.2s ease;
    }
    a:hover {
        color: var(--col-ok);
    }

    *, *::before, *::after {
        box-sizing: border-box;
    }

    @keyframes scroll {
        0% {
            transform: translateX(0);
        }
        100% {
            transform: translateX(-50%);
        }
    }
</style>
