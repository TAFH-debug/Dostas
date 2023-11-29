<nav class="header">
    <a class="logo" href="/home">DOSTAS</a>
    <a href="/home">About Us</a>
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
        border-bottom: rgba(252,176,69,1) solid thin ;
    }

    .logo {
        font-weight: bolder;
        font-family: Impact, Haettenschweiler, 'Arial Narrow Bold', sans-serif;
        font-size: 40px;
        background: -webkit-linear-gradient(0deg, rgba(131,58,180,1) 0%, rgba(253,29,29,1) 50%, rgba(252,176,69,1) 100%);
  		-webkit-background-clip: text;
  		-webkit-text-fill-color: transparent;
        background-size: 200% 100%;
        transition: background-position 1s ease-in;
        
    }
    .logo:hover {
        background-position: 100% 0;
    }

    a {
        text-decoration: none;
        outline: none;
        color: #FCB045;
        font-family: 'Courier New', Courier, monospace;
        font-size: 1.7vw;
        transition: all 0.25s ease-in-out;
    }

    .header * {
        padding: 10px;
        margin: 10px;
    }

    a:hover {
        /* transform: translateY(-20%); */
        transform: translate(10%);
        color: #fcc373;
    }
</style>