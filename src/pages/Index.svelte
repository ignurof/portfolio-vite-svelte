<script>
	import Card from "../lib/Card.svelte"
</script>

<div class="page-content">
	<div class="cards">
		<Card />
		<Card />
		<Card />
		<Card />
		<Card />
		<Card />
	</div>
</div>

<style>
	.page-content {
		display: flex;
		flex-direction: column;
		border: 2px solid red;
	}

	.cards {
		display: flex;
		flex-direction: row;
		flex-flow: row wrap;
		border: 2px solid white;
	}
</style>
