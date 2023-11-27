<nav class="header">
    <a class="logo" href="/home">DOSTAS</a>
    <a href="/home">Ref 1</a>
    <a href="/about">Ref 2</a>
    <a href="/policy">Ref 3</a>
</nav>

<style>
    .header {
        width: 100%;
        background: black;
        display: flex;
        flex-direction: row;
        align-items: center;
    }

    .logo {
        font-weight: bolder;
        font-family: Impact, Haettenschweiler, 'Arial Narrow Bold', sans-serif;
        font-size: 40px;
        background: -webkit-linear-gradient(0deg, rgba(131,58,180,1) 0%, rgba(253,29,29,1) 50%, rgba(252,176,69,1) 100%);
  		-webkit-background-clip: text;
  		-webkit-text-fill-color: transparent;
    }

    a {
        text-decoration: none;
        outline: none;
        color: #FCB045;
        font-family: 'Courier New', Courier, monospace;
        font-size: 25px;
    }

    .header * {
        padding: 10px;
        margin: 10px;
    }
</style>