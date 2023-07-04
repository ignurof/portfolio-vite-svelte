<script>
	import svelteLogo from "./assets/svelte.svg";
	import viteLogo from "/vite.svg";
	import Index from "./pages/Index.svelte";
	import About from "./pages/About.svelte";

	let loremIpsum = "";

	const getLoremIpsum = async () => await fetch("http://localhost:5173/lorem.txt")
		.then((response) => response.text())
		.then((data) => {
			return data;
		})
		.catch((error) => console.error("ERROR: getLoremIpsum"));

	getLoremIpsum().then((data) => {
		loremIpsum = data;
	});

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
	}

</script>

<main>
	<header>
		<div class="site-logo">ignurof</div>
		<nav>
			<ul>
				<li>
					<button on:click={() => updateActivePage("index")}>Index</button>
				</li>
				<li>
					<button on:click={() => updateActivePage("about")}>About</button>
				</li>
			</ul>
		</nav>
	</header>

	<div class="active-page">
		{#if activePage === "index"}
			<!-- loremIpsum={loremIpsum} same as below -->
			<Index {loremIpsum} />
		{:else if activePage === "about"}
			<About {loremIpsum} />
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
		flex-direction: column;
	}

	header {
		display: flex;
		min-width: 100%;
		align-items: center;
		padding-top: 2rem;
		padding-bottom: 2rem;
	}

	.site-logo {
		font-size: 2rem;
		padding-left: 4rem;
	}

	nav {
		display: flex;
		justify-content: flex-end;
		width: 100%;
		padding-right: 2rem;
	}

	nav ul {
		list-style-type: none;
		margin: 0;
		display: flex;
		justify-content: center;
		align-items: center;
	}

	nav ul li {
		padding-left: 2rem;
		padding-right: 2rem;
	}

	button {
		color: white;
		background-color: transparent;
		border: none;
		margin: 0;
		padding: 0;
		text-align: inherit;
		font: inherit;
		border-radius: 0;
		appearance: none;
	}

	button:hover {
		color: black;
		cursor: pointer;
	}

	.active-page {
		max-width: 1280px;
		margin: 0 auto;
	}

	footer {
		width: 100%;
		margin: 0 auto;
		display: flex;
		justify-content: center;
		align-items: center;
		padding-top: 4rem;
		padding-bottom: 4rem;
	}
</style>
