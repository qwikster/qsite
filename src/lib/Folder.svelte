<script>
    export let name
    let open = false
</script>

<div class="folder">
    <button aria-expanded={open} on:click={() => open = !open}>{name}
        <svg viewBox="0 0 20 20" fill="none" >
        <path class="vert" d="M10 1V19" stroke="black" stroke-width="2"/>
        <path d="M1 10L19 10" stroke="black" stroke-width="2"/>
        </svg>
    </button>

    <div class="contents" hidden={!open}>
        <slot></slot>
    </div>
</div>

<style>

</style>
