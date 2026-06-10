<script></script>

<div class="links">
    <div class="link-list">
        <div class="email link">
            <span class="icon" style="color: var(--col-accent);">󰇮</span>
            <span class="title">You can email</span>
            <div class="email">
                <a href="mailto:me@qwik.top" ><span class="code">me@qwik.top</span></a>
            </div>
        </div>
        <div class="discord link">
            <span class="icon" style="color: #5865F2;"></span>
            <span class="title">Fastest response</span>
            <div class="discord-link">
                <a target="_blank" href="https://discord.com/users/721037730905325628" ><span class="code">i_qwik</span></a>
                on Discord
            </div>
        </div>
        <div class="github link">
            <span class="icon" style="color: #F2F5F3;"></span>
            <span class="title">My GitHub</span>
            <div class="email">
                <a target="_blank" href="https://github.com/qwikster" ><span class="code">qwikster</span></a>
            </div>
        </div>
    </div>
    <span class="request">Please contact me if you need a name or phone number!</span>
</div>

<style>
    .links {
        font-family: var(--ff-info);
        font-size: var(--font-small);
        color: var(--col-body);
        display: flex;
        flex-direction: column;
        line-height: 1.3;
        text-align: center;
        justify-content: center;
    }

    .link-list {
        display: flex;
        text-align: center;
        justify-content: center;
        gap: 12px;
        padding: 12px 0px;
    }

    .link {
        display: flex;
        flex-direction: column;
    }

    .icon {
        font-size: var(--font-header);
    }

    .title {
        font-weight: bold;
    }

    .request {
        font-family: var(--ff-body);
        padding-bottom: var(--pad-ui);
    }

    .code {
        color: var(--col-hover);
        border: 1px solid var(--bg-2);
        border-radius: var(--border-panel);
        background-color: var(--bg-0);
        padding: 0px 4px;
        transition: ease 0.2s all;
    }

    .code:hover { color: var(--col-header); }
    a { text-decoration: none; }

    .discord {
        padding: 0px 12px;
        border-left: var(--border-hr) solid var(--col-header);
        border-right: var(--border-hr) solid var(--col-header);
    }
</style>
