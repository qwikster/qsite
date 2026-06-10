<script>
  import { onMount } from "svelte";
  let time = $state(new Date());

  let id = "loading"
  let date = "loading"
  let error = ""

  onMount(async () => {
    try {
      const response = await fetch(
        `https://api.github.com/repos/qwikster/qsite/commits`,
        {headers: {"Accept": "application/vnd.github+json"}}
      );
      if (!response.ok) throw new Error(`failed to fetch GitHub info: ${response.statusText}`)
      const data = await response.json();

      if (data && data.length > 0) {
        id = data[0].sha.substring(0, 7);
        date = new Date(data[0].commit.author.date).toLocaleTimeString()  + " " + new Date(data[0].commit.author.date).toLocaleDateString()
      }
    } catch (err) {
      error = err.message;
    }
  });

  onMount(() => {
    const interval = setInterval(() => {
      time = new Date();
    }, 1000);
    return() => clearInterval(interval)
  })
</script>

<div class="etc">
    <div class="item github">
        <div>
            commit <b class="time">{id}</b> at
        </div>
        <div>
            <b class="time">{date}</b> on
        </div>
        <div class="git-link">
            <span class="icon" style="color: #F2F5F3;"></span>
            <b><a target="_blank" href="https://github.com/qwikster/qsite">qwikster/qsite</a></b>
        </div>
    </div>
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

    .git-link {
        display: flex;
        justify-content: center;
        gap: var(--pad-text);
        align-items: center;
    }

    .icon { font-size: var(--font-header); }
    a { color: var(--col-hover); }
</style>
