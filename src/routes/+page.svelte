<div class="title">Dostas</div>
<style>
	@keyframes sparkle {
  		0% {
    		transform: scale(0);
  		}

  		60% {
    		transform: scale(1) translate(4px, 1px) rotate(8deg);
  		}

  		100% {
    		transform: scale(0) translate(4px, 1px) rotate(8deg);
  		}
	}

	.title {
		font-family: 'Courier New', Courier, monospace;
		font-size: 100px;
		font-weight: bold;
		color: #0A2463;

		animation: sparkle 0.4s linear 3.5s 1 forwards;
	}
</style>
