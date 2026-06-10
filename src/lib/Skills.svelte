<script>
    import { onMount } from "svelte";

    let skills = $state([])

    onMount(async () => {
      try {
        const response = await fetch('/skills.json');
        skills = await response.json()
      } catch (error) {
        console.error("Failed to load skills:", error)
      }
    });
</script>

<div class="skills">
    <div class="skill-tier">
        <div class="skill-desc" style="color: var(--col-ok);">
             good&nbsp;at!
        </div>
        <div class="skill-list">
            <div class="skill-line" style="color: var(--bg-ok);">
                {#each skills.find(t => t.tier === "ok")?.items ?? [] as skill}
                    <span class="skill">{skill}</span>
                {/each}
            </div>
        </div>
    </div>
    <div class="skill-tier">
        <div class="skill-desc" style="color: var(--col-meh);">
            <div class="skill-text">󰜥&nbsp;learn as&nbsp;needed</div>
        </div>
        <div class="skill-list">
            <div class="skill-line" style="color: var(--bg-meh);">
                {#each skills.find(t => t.tier === "meh")?.items ?? [] as skill}
                    <span class="skill">{skill}</span>
                {/each}
            </div>
        </div>
    </div>
    <div class="skill-tier">
        <div class="skill-desc" style="color: var(--col-wait);">
            <div class="skill-text">&nbsp;still learning</div>
        </div>
        <div class="skill-list">
            <div class="skill-line" style="color: var(--bg-wait);">
                {#each skills.find(t => t.tier === "wait")?.items ?? [] as skill}
                    <span class="skill">{skill}</span>
                {/each}
            </div>
        </div>
    </div>
    <div class="skill-tier">
        <div class="skill-desc" style="color: var(--col-bad);">
            <div class="skill-text">&nbsp;don't like&nbsp;using</div>
        </div>
        <div class="skill-list">
            <div class="skill-line" style="color: var(--bg-bad);">
                {#each skills.find(t => t.tier === "bad")?.items ?? [] as skill}
                    <span class="skill">{skill}</span>
                {/each}
            </div>
        </div>
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
        display: grid;
        grid-template-columns: auto 1fr;
        align-items: stretch;
    }

    .skill-desc {
        background-color: var(--bg-0);
        font-family: var(--ff-info);
        font-size: var(--font-small);
        border: 1px solid var(--bg-2);
        border-radius: var(--border-panel);
        padding: var(--pad-text);
        margin-right: var(--pad-ui);
        display: flex;
        align-items: center;
    }

    .skill-list {
        display: flex;
        flex-direction: column;
        justify-content: center;
    }

    .skill-line {
        display: flex;
        flex-wrap: wrap;
        gap: var(--pad-tiny);
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
</style>
