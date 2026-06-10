        <div class="skill-container">
            <div class="skill-legend">
                <div class="skill-desc">
                    <span class="skill-icon" style="color: var(--col-ok)"></span>
                    <span class="skill-key" style="color: var(--bg-ok)">good at!</span>
                </div>

                <div class="skill-desc">
                    <span class="skill-icon" style="color: var(--col-meh)">󰜥</span>
                    <span class="skill-key" style="color: var(--bg-meh)">will learn as needed</span>
                </div>

                <div class="skill-desc">
                    <span class="skill-icon" style="color: var(--col-wait)"></span>
                    <span class="skill-key" style="color: var(--bg-wait)">learning basics</span>
                </div>

                <div class="skill-desc">
                    <span class="skill-icon" style="color: var(--col-bad)"></span>
                    <span class="skill-key" style="color: var(--bg-bad)">prefer not to use</span>
                </div>
            </div>
            <div class="skills">
                <div class="skill-item">
                    <span class="skill-icon" style="color: var(--col-ok)"></span>
                    <span class="skill">Linux</span>
                </div>
                <div class="skill-item">
                    <span class="skill-icon" style="color: var(--col-ok)"></span>
                    <span class="skill">Python</span>
                </div>
                <div class="skill-item">
                    <span class="skill-icon" style="color: var(--col-ok)"></span>
                    <span class="skill">HTML+CSS</span>
                </div>
                <div class="skill-item">
                    <span class="skill-icon" style="color: var(--col-meh)">󰜥</span>
                    <span class="skill">Arduino</span>
                </div>
                <div class="skill-item">
                    <span class="skill-icon" style="color: var(--col-meh)">󰜥</span>
                    <span class="skill">Sysadmin</span>
                </div>
                <div class="skill-item">
                    <span class="skill-icon" style="color: var(--col-meh)">󰜥</span>
                    <span class="skill">Networking</span>
                </div>
                <div class="skill-item">
                    <span class="skill-icon" style="color: var(--col-meh)">󰜥</span>
                    <span class="skill">Svelte</span>
                </div>
                <div class="skill-item">
                    <span class="skill-icon" style="color: var(--col-meh)">󰜥</span>
                    <span class="skill">JavaScript</span>
                </div>
                <div class="skill-item">
                    <span class="skill-icon" style="color: var(--col-meh)">󰜥</span>
                    <span class="skill">Onshape</span>
                </div>
                <div class="skill-item">
                    <span class="skill-icon" style="color: var(--col-wait);"></span>
                    <span class="skill">C++</span>
                </div>
                <div class="skill-item">
                    <span class="skill-icon" style="color: var(--col-wait);"></span>
                    <span class="skill">Rust</span>
                </div>
                <div class="skill-item">
                    <span class="skill-icon" style="color: var(--col-wait);"></span>
                    <span class="skill">Engineering</span>
                </div>
                <div class="skill-item">
                    <span class="skill-icon" style="color: var(--col-wait);"></span>
                    <span class="skill">Auto Repair</span>
                </div>
                <div class="skill-item">
                    <span class="skill-icon" style="color: var(--col-bad);"></span>
                    <span class="skill">TypeScript</span>
                </div>
                <div class="skill-item">
                    <span class="skill-icon" style="color: var(--col-bad);"></span>
                    <span class="skill">React</span>
                </div>
            </div>
        </div>


<style>
    .skill-container {
        display: flex;
    }

    .skill-legend {
        display: flex;
        flex-direction: column;
        gap: var(--pad-ui);
        justify-content: center;
        align-items: center;
        padding: var(--pad-ui) 0px;
    }

    .skill-desc {
        background-color: var(--bg-0);
        font-family: var(--ff-info);
        font-size: var(--font-tiny);
        padding: 2px;
        border-radius: var(--round-button);
    }

    .skill-key {
        display: flex;
        flex-direction: column;
    }

    .skills {
        display: flex;
        align-items: center;
        justify-content: center;
        flex-wrap: wrap;
        gap: 12px;
        padding: var(--pad-text) 0px;
    }

    .skill-item {
        color: var(--col-dim);
        font-family: var(--ff-info);
        font-size: var(--font-tiny);

        display: flex;
        flex-direction: column;
        border: var(--border-small) dashed var(--col-border);
        padding: 2px;
        border-radius: var(--round-panel);
    }
</style>
