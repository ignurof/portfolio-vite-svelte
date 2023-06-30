<script>
	import svelteLogo from "./assets/svelte.svg";
	import viteLogo from "/vite.svg";
	import Index from "./pages/Index.svelte";
	import About from "./pages/About.svelte";
	//import loremIpsum from "./assets/lorem.txt"; output: /src/assets/lorem.txt

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
		width: 100vw;
	}

	header {
		display: flex;
		min-width: 100%;
		border-bottom: 4px solid black;
		background-color: purple;
	}

	.site-logo {
		font-size: 4rem;
		background-color: green;
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
		padding: 0;
		display: flex;
		background-color: cyan;
		justify-content: center;
		align-items: center;
		border-left: 4px solid black;
	}

	.active-page {
		max-width: 1280px;
	}

	footer {
		position: absolute;
		bottom: 0;
		width: 100%;
		height: 2.5rem;
	}
</style>
