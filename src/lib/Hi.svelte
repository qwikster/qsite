<script>

</script>

<div class="hi">
    <div class="hi-left">
        <span class="hi_l">&nbsp;</span>
        <span class="hi_hi"><b>hi,</b></span>
        <span class="hi_hi">i'm</span>
        <span class="hi_qwik"><b>qwik</b></span>
        <span class="hi_hi">!</span>
    </div>
    <div class="hi-right">
        <!-- <img src="ca.svg" alt="Canada!" width="22px"> -->
        <span class="flag-ca"></span>
        <span class="flag-at">@</span>
        <span class="flag-timezone">EST</span>
    </div>
</div>

<style>
    .hi {
        display: flex;
        justify-content: space-between;
        color: var(--col-body);
        font-family: var(--ff-header), monospace;
        font-size: var(--font-header);
        margin: 0px;
        padding: 2px;
        line-height: 1.3;
    }

    .hi-left {
        display: flex;
        align-items: center;
    }

    .hi-right {
        display: flex;
        align-items: center;
        border: 1px solid var(--bg-2);
        border-radius: var(--border-panel);
        background-color: var(--bg-0);
        padding: 0px 4px;
        padding-left: 6px;
    }

    .hi_l {
        color: var(--col-accent);
    }

    .hi_hi {
        color: var(--col-header);
        margin-right: 8px;
    }

    .hi_qwik {
        color: var(--col-accent);
        border: 1px solid var(--bg-2);
        border-radius: var(--border-panel);
        background-color: var(--bg-0);
        padding: 0px 4px;
    }

    .flag-ca {
        color: var(--flag-ca);
        font-size: var(--font-header);
    }

    .flag-at {
        color: var(--col-dim);
        font-size: var(--font-tiny);
        padding: 0px 8px;
    }

    .flag-timezone {
        color: var(--col-header);
        font-size: var(--font-text);
        font-weight: bold;
    }

    @media (max-width: 380px) {
        .hi {
            font-size: var(--font-text);
        }
        .flag-timezone {
            font-size: var(--font-tiny);
        }
    }

</style>
