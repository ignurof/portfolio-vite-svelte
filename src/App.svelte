<script>
	//import svelteLogo from './assets/svelte.svg'
	//import viteLogo from '/vite.svg'
	//import Counter from './lib/Counter.svelte'

	let activePage = -1;
	let pages = { 
		"index": 0,
		"about": 1
	};

	const testCall = () => {
		console.log("Test");
	};
</script>

<main>
	<nav>
		<button>Index</button>
		<button on:click={() => testCall()}>About</button>
	</nav>

	<!-- Site Content -->
	<!-- <Index /> -->

	<footer>
		- ignurof
	</footer>
</main>

<style>
</style>
