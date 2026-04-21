<script>
	import favicon from '$lib/assets/favicon.svg';

	let { children } = $props();
</script>

<svelte:head>
	<link rel="icon" href={favicon} />
</svelte:head>

<header>
	<h1>Meet miffy</h1>
</header>

{@render children()}

<footer></footer>

<style>
	header {
		height: 15rem;
		background-color: var(--OceanBlue);
	}
	footer {
		background-color: var(--TreeGreen);
		height: 15rem;
	}
</style>
