<script>
  import { onMount } from "svelte";
  let time = $state(new Date());

  onMount(() => {
    const interval = setInterval(() => {
      time = new Date();
    }, 1000);
    return() => clearInterval(interval)
  })
</script>

<div class="etc">
    <div class="item timezone">
        <div class="tz">
            <span class="time">{time.toLocaleTimeString([], {timeZone: "America/Toronto", hour12: true, timeStyle: 'short'})}</span>
            <span class="tz-title">ME</span>
        </div>
        <div class="tz">
            <span class="time">{time.toLocaleTimeString([], {hour12: true, timeStyle: 'short'})}</span>
            <span class="tz-title">YOU</span>
        </div>
        <div class="tz">
            <span class="time">{time.toLocaleTimeString([], {timeZone: "UTC", hour12: false})}</span>
            <span class="tz-title">UTC</span>
        </div>
    </div>
    <div class="item github">

    </div>
</div>


<style>
    .etc {
        font-family: var(--ff-info);
        font-size: var(--font-small);
        color: var(--col-body);
        display: flex;
        line-height: 1.3;
        text-align: center;
        justify-content: center;
        padding: var(--pad-ui);
        gap: var(--pad-ui);
    }

    .time {
        color: var(--col-accent);
        border: 1px solid var(--bg-2);
        border-radius: var(--border-panel);
        background-color: var(--bg-0);
        padding: 0px 4px;
        margin-right: 4px;
        transition: ease 0.2s all;
    }

    .item {
        padding-right: var(--pad-ui);
        border-right: var(--border-hr) solid var(--col-header);
    }

    .tz {
        display: flex;
        justify-content: space-between;
    }
</style>
