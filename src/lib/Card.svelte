<script>
	export let cardNum = 0;

	let imageSrc = "https://img.freepik.com/premium-vector/construction-sign-label_24886-506.jpg"; 
</script>

<div class="card">
	<div class="head">
		<img src={imageSrc} alt="placeholder alt desc" />
	</div>
	<div class="content">
		<h4>Titlebar Here: Boogaloo</h4>	
		<p>Card #{cardNum}</p>
	</div>
</div>

<style>
	.card {
		border: 4px solid pink;
		border-radius: 2rem;
		overflow: hidden;
		display: flex;
		flex-direction: column;
	}

	.head {
	}

	img {
		width: 100%;
		height: 100%;
	}

	.content {
		border-top: 2px solid black;
	}

</style>
