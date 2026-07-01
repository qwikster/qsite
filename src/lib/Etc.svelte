<script>
  import { onMount } from "svelte";
  let time = $state(new Date());

  // svelte-ignore non_reactive_update
  let id = "loading"
  // svelte-ignore non_reactive_update
  let date = "loading"
  let error = ""
  let slackID = "U091JJ2JF8E"

  function format(seconds) {
    const h = Math.floor(seconds / 3600);
    const m = Math.floor((seconds % 3600) / 60);
    return `${h}h&nbsp;${m}m`;
  }

  async function get_hackatime(id) {
    const alltime = await fetch(`https://hackatime.hackclub.com/api/v1/users/${id}/stats`);
    const alltimedata = await alltime.json()

    const weektime = new Date();
    weektime.setDate(weektime.getDate() - 7)
    const param_start = weektime.toISOString().split("T")[0];
    const param_end = new Date().toISOString().split("T")[0];

    const week = await fetch(`https://hackatime.hackclub.com/api/v1/users/${id}/stats?start_date=${param_start}&end_date=${param_end}`)
    const weekdata = await week.json()

    const alltime_seconds = alltimedata.data.total_seconds || 0;
    const week_seconds = weekdata.data.total_seconds || 0;

    return {
      total: format(alltime_seconds),
      week: format(week_seconds)
    }
  }

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
        date = new Date(data[0].commit.author.date).toLocaleTimeString(
          [], {hour12: true, timeStyle: 'short'}
        )
        + " " +
        new Date(data[0].commit.author.date).toLocaleDateString();
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

  let stats = get_hackatime(slackID);
</script>

<div class="etc">
    {#await stats}
        <div class="item hackatime">loading Hackatime...</div>
    {:then data}
        <div class="item hackatime">
            <span class="code-time">
                 coding time
            </span>
            <div class="time-item">
                <span>all:&nbsp;</span>
                <span class="time">{@html data.total}</span>
            </div>
            <div class="time-item">
                <span>week:&nbsp;</span>
                <span class="time">{@html data.week}</span>
            </div>
        </div>
    {:catch time_error}
        <div class="item hackatime">error loading Hackatime :(</div>
    {/await}

    <div class="item github">
        <div>
            commit <b class="time">{id}</b> at
        </div>
        <div>
            <b class="time">{date}</b>
        </div>
        <div class="git-link">
            on
            <span class="icon" style="color: #F2F5F3;"></span>
            <b><a target="_blank" href="https://github.com/qwikster/qsite">qwikster/<wbr>qsite</a></b>
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
        flex-wrap: wrap;
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

    .code-time {
        border-bottom: var(--border-hr) solid var(--col-secondary);
        align-self: center;
        margin-right: 6px;
        margin-bottom: 2px;
        font-size: var(--font-tiny);
        color: var(--col-ok);
    }

    .item {
        display: flex;
        flex-direction: column;
        justify-content: center;
        padding-right: var(--pad-ui);
    }

    @media (min-width: 610px) {
        .item {
            border-right: var(--border-hr) solid var(--col-header);
        }
        .item:last-child {
            border-right: none;
            padding-right: 0;
        }
    }

    @media (max-width: 609px) {
        .etc {
            flex-direction: column;
            align-items: center;
        }
        .item {
            padding-right: 0px;
            width: 100%;
            max-width: 280px;
            padding-bottom: var(--pad-ui);
            border-bottom: var(--border-hr) solid var(--col-header);
        }
        .item:last-child {
            border-bottom: none;
            padding-bottom: 0;
        }
        .tz, .time-item {
            padding: 0px 2rem;
        }
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

    .time-item {
        display: flex;
        justify-content: space-between;
    }

    .icon { font-size: var(--font-header); }
    a { color: var(--col-hover); }
</style>
