<script>
  import Header from "./Header.svelte";

</script>

<Header/>
<div class="body">
	<div class="segment">
		<h1>
			What is <span class="app_name">Dostas</span>?
		</h1>
		<p>
			Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. 
			Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. 
			Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. 
			Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.
		</p>
	</div>
	<div>
		<h1>

		</h1>
	</div>
</div>
<style>
	.segment {
		padding: 20px;
		height: 50%;
		display: flex;
		flex-direction: row;
		color: black;
	}
	
	.app_name {
		font-family: Impact, Haettenschweiler, 'Arial Narrow Bold', sans-serif;
	}

	h1 {
  		font-size: 72px;
  		background: -webkit-linear-gradient(0deg, rgba(131,58,180,1) 0%, rgba(253,29,29,1) 50%, rgba(252,176,69,1) 100%);
  		-webkit-background-clip: text;
  		-webkit-text-fill-color: transparent;
	}

	.segment p {
		text-align: right;
		margin-left: auto;
		margin-right: auto;
		width: 50%;
		font-size: 25px;
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
</style>
