<script>
  import Header from "./Header.svelte";
</script>

<Header/>
<link rel="stylesheet" href="https://fonts.googleapis.com/css?family=Poppins">
<div class="body">
	<div class="segment">
		<h1>
			What is <span class="app_name">ProjectName</span>?
		</h1>
		<p>
			Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. 
			Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. 
			Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. 
			Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.
		</p>
	</div>
	<div class="segment">
		<p id="l">
			ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. 
			Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. 
			Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. 
			Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.
		</p>
		<h1>
			What do we offer?
		</h1>
	</div>
	<div class="segment" id="reg">
		<button>
			Register
		</button>
		<h1>
			Not Convinced?
		</h1>
		<h2>Learn more:</h2>
	</div>	
</div>
<style>
	.body {
        background-color: #020b0f;
    }
	
	.segment {
		padding: 20px;
		height: 50%;
		display: flex;
		flex-direction: row;
		color: black;
		font-family: "Poppins", sans-serif;	
	}
	
	.app_name {
		font-size: bolder;
	}

	h1 {
  		font-size: 4vw;
  		background: -webkit-linear-gradient(0deg, rgba(131,58,180,1) 0%, rgba(253,29,29,1) 50%, rgba(252,176,69,1) 100%);
  		-webkit-background-clip: text;
  		-webkit-text-fill-color: transparent;
	}

	.segment p {
		color: aliceblue;
		text-align: right;
		margin-left: auto;
		margin-right: auto;
		width: 50%;
		font-size: 1.4vw;
		height: 100%;
		transform: translateY(50%);
		border-radius: 50px;
	}

	.segment h1 {
		padding-top: 50px;
		padding-bottom: 50px;
		margin-left: auto;
		margin-right: auto;
		transform: translateY(50%);
	}

	.segment * {
		padding: 10px;
	}
	#l {
		text-align: left;
	}



	#reg {
		align-items: center;
		justify-content: center;
		flex-direction: column;
		color: aliceblue;
	}
	.segment button {
		background-color: #000000;
		border: solid rgba(253,29,29,1);
		border-radius: 1vw;
		color: aliceblue;
		font-family: "Poppins", sans-serif;
		padding: 30px 100px;
		transform: translateY(100%);
		border-radius: 2vw;
		font-size: 2vw;
		transition: all 0.3s ease;
	}
	.segment button:hover {
		border-radius: 3vw;
		border: solid rgba(252,176,69,1);
		color: white;
	}
	#reg h1 {
		transform: translateY(0%);
		width: fit-content;
		margin: 6% 0% 0%;
	}
	#reg h2 {
		margin-top: 0;
		transform: translateY(-100%);
	}
</style>
