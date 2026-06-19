<script>
    export let name
    export let open = true
</script>

<div class="folder">
    <button class="stripes-sm" aria-expanded={open} on:click={() => open = !open}>
        <span class="name">{name}</span>
        <svg viewBox="0 0 20 20" fill="none" >
        <path class="vert" d="M10 1V19" stroke="var(--col-header)" stroke-width="2"/>
        <path d="M1 10L19 10" stroke="var(--col-header)" stroke-width="2"/>
        </svg>
    </button>

    <div class="content" hidden={!open}>
        <slot></slot>
    </div>
</div>

<style>
    .folder {
        display: flex;
        flex-direction: column;
        border: var(--border-small) solid var(--col-border);
        border-radius: var(--round-panel);
        margin: var(--pad-ui) 0px;
    }

    .name {
        padding-left: 10px;
        align-self: flex-start;
    }

    button {
        display: flex;
        flex: 1;
        border: none;
        border-radius: var(--round-panel);
        background-color: var(--bg-2);
        font-family: var(--ff-button);
        color: var(--col-body);
        padding: var(--pad-text) 0px;
        justify-content: space-between;
    }

    button[aria-expanded="true"] {
        border-radius: 10px 10px 0px 0px;
        border-bottom: var(--border-small) dashed var(--col-secondary);
    }

    button[aria-expanded="true"] .vert {
        display: none;
    }

    svg {
        height: 12px;
        width: 12px;
        padding-right: 10px;
    }
</style>
