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
		border: 2px solid red;
		display: flex;
		flex-direction: column;
	}

	header {
		display: flex;
		min-width: 100%;
		border-bottom: 4px solid black;
		background-color: purple;
	}

	.site-logo {
		font-size: 2rem;
		background-color: green;
		padding: 2rem;
	}

	nav {
		display: flex;
		justify-content: flex-end;
		background-color: red;
		width: 100%;
	}

	nav ul {
		list-style-type: none;
		margin: 0;
		padding: 2rem;
		display: flex;
		background-color: cyan;
		justify-content: center;
		align-items: center;
		border-left: 4px solid black;
	}

	nav ul li {
		padding-left: 2rem;
		padding-right: 2rem;
	}

	button {
		background-color: white;
		color: black;
		border: 2px solid black;
	}

	button:hover {
		background-color: black;
		color: white;
	}

	.active-page {
		max-width: 1280px;
		border: 2px dotted pink;
		margin: 0 auto;
	}

	footer {
		width: 100%;
		height: 2.5rem;
		margin: 0 auto;
		border: 2px solid cyan;
		display: flex;
		justify-content: center;
		align-items: center;
		padding-top: 4rem;
		padding-bottom: 4rem;
	}
</style>
