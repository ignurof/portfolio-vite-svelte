<script>
	//import svelteLogo from './assets/svelte.svg'
	//import viteLogo from '/vite.svg'
	//import Counter from './lib/Counter.svelte'

	let siteContent = "index";

	const updateSiteContent = (pageName) => {
		switch(pageName){
			case "index":
				siteContent = "index";
				break;
			case "about":
				siteContent = "about";
				break;

			default:
				console.error("updateSiteContent error");
		}
	};
</script>

<main>
	<nav>
		<button on:click={() => updateSiteContent("index")}>Index</button>
		<button on:click={() => updateSiteContent("about")}>About</button>
	</nav>

	<!-- Site Content -->
	<!-- <Index /> -->
	{#if siteContent === "index"}
		<Index />
	{:else if siteContent === "about"}
		<About />
	{:else}
		{console.error("SiteContent HTML section error")}
	{/if}	

	<footer>
		- ignurof
	</footer>
</main>

<style>
</style>
