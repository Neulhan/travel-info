<script>
	import { onMount, setContext } from "svelte";
	import { mapbox, key } from "./mapbox.js";

	setContext(key, {
		getMap: () => map,
	});

	export let lat;
	export let lon;
	export let zoom;

	let container;
	let map;

	onMount(() => {
		const link = document.createElement("link");
		link.rel = "stylesheet";
		link.href = "https://unpkg.com/mapbox-gl/dist/mapbox-gl.css";

		link.onload = () => {
			map = new mapbox.Map({
				container,
				style: "mapbox://styles/mapbox/streets-v9",
				center: [lon, lat],
				zoom,
			});
		};

		document.head.appendChild(link);

		return () => {
			map.remove();
			link.parentNode.removeChild(link);
		};
	});
</script>

<nav>
	<ul class="nav-container">
		<li class="nav-item">Travel-Info</li>
		<form>
			<input type="search" placeholder="Search" aria-label="Search" />
			<button type="submit">Search</button>
		</form>
	</ul>
</nav>

<div class="mapbox" bind:this={container}>
	{#if map}
		<slot />
	{/if}
</div>

<style>
	.mapbox {
		width: 100%;
		height: 100%;
	}
	.nav-container {
		display: flex;
		flex-direction: row;
		width: 100%;
		margin: 0;
		padding: 0;
		list-style-type: none;
	}
	.nav-item {
		padding: 15px;
	}
	form {
		display: flex;
		align-items: flex-end;
	}
</style>
