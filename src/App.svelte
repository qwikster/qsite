<script>
    import logo from "/favicon.png"
</script>

<div class="content">
    <div class="header">
        <hr><div class="textbox">things</div><hr><img src={logo} alt="logo"><hr><div class="textbox">blag</div><hr>
    </div>
    <div class="textbox">
        <h1 class="text">welcome to my cool site :)</h1>
        <p class="text">this is a bunch of long text that i can put in the middle of the website to show the things that the text is saying like who i am and what the point of this site in and how much random shit i can type</p>
        <div class="textbox">
            <h1>links             (expand)</h1>
        </div>
        <div class="textbox">
            <h1>88x31s             (expand)</h1>
        </div>
        <div class="textbox">
            <h1>etc             (close)</h1>
            <hr>
            <p>ooo time zones and music player and uptime neat</p>
        </div>
        <p>i was going to put some scrolling icon buttons here to show cool things i use</p>
    </div>
    <div class="links">
        <a href="https://youtube.com/@qwiksteryt">youtube!</a>
        <a href="https://qwik.top">you are here!</a>
        <a href="https://github.com/qwikster">github!</a>
    </div>
</div>

<style>
    .header {
        display: flex;
        flex-direction: row;
        align-items: center;
        justify-content: space-between;
    }

    hr {
        border-width: var(--border-small) 0px 0px 0px;
        border-style: solid;
        border-color: var(--secondary);
        margin: 0px 1vw;
        width: auto;
        flex-grow: 1;
    }

    .textbox {
        background-color: var(--bg);
        padding: 1vmin;
        margin-bottom: 2vmin;
        border: var(--border-tile) solid var(--dim);

    }

    .content {
        margin-bottom: 50vh;
    }

    .text {
        padding: 0px;
        margin: 0.3rem 0px;
        text-align: center;
    }

    .links {
        display: flex;
        justify-content: space-evenly;
        font-size: var(--font-para);
    }

    a {
        color: var(--accent);

    }

    h1 {font-size: var(--font-header);}
    p  {font-size: var(--font-para);}
    img {height: 10vmin; padding: 1vw;}

</style>
