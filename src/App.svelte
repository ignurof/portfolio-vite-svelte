<script>
	import svelteLogo from './assets/svelte.svg'
	import viteLogo from '/vite.svg'
	import Index from './pages/Index.svelte'
	import About from './pages/About.svelte'

	let activePage = "index";

	const updateActivePage = (pageName) => {
		switch(pageName){
			case "index":
				activePage = "index";
				break;
			case "about":
				activePage = "about";
				break;

			default:
				console.error("updateActivePage error");
		}
	};
</script>

<main>
	<header>
		<h2>ignurof portfolio</h2>
		<nav>
			<button on:click={() => updateActivePage("index")}>Index</button>
			<button on:click={() => updateActivePage("about")}>About</button>
		</nav>
	</header>

	<div class="active-page">
		{#if activePage === "index"}
			<Index />
		{:else if activePage === "about"}
			<About />
		{:else}
			{console.error("active-page div expression error")}
		{/if}
	</div>

	<footer>
		made by ignurof, powered by <img src={viteLogo} /> + <img src={svelteLogo} />
	</footer>
</main>

<style>
	main {
		display: flex;
		border: 2px solid red;
	}

	header {

	}

	nav {

	}

	.active-page {
		background-color: gray;
	}

	footer {

	}
</style>
