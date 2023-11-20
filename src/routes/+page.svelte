<script>
  import Header from "./Header.svelte";

</script>

<Header/>
<div class="body">
	<div class="segment">
		<img src="https://source.unsplash.com/random/200x200?sig=1" alt="None"/>
		<p>
			Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. 
			Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. 
			Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. 
			Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.
		</p>
	</div>
</div>
<style>
	.segment {
		display: flex;
		flex-direction: row;
		color: #576460;
	}

	.segment p {
		text-align: center;
		margin-left: auto;
		margin-right: auto;
		width: 50%;
		font-size: 25px;
		height: 100%;
	}

	.segment img {
		width: 40%;
	}

	.segment * {
		padding: 10px;
	}
</style>
