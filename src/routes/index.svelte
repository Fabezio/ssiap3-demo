<script context="module" lang="ts">
	export const prerender = true;
</script>

<script lang="ts">
	// import Counter from '$lib/Counter.svelte';
	let effectif = 0
	let D = 0
	let UP = 0
	function calculer ()  {
		if (100 > effectif && effectif <= 500) {
			D = 2
			UP = Math.ceil(effectif / 100) + 1
		}
		else if (effectif > 500) {
			D = Math.ceil(effectif /  500) + 1
			UP = Math.ceil(effectif / 100)
		}
		// return (D, UP)
	}
	function handleKey (e: {key: string}) {
		if (e.key === 'Enter') {
			// e.preventDefault()
			calculer()
		
		}
	}
</script>

<svelte:head>
	<title>Home</title>
	<meta name="description" content="Svelte demo app" />
</svelte:head>

<section>
	<h1>
		calcul des dégagements
		<!-- <span class="welcome">
			<picture>
				<source srcset="svelte-welcome.webp" type="image/webp" />
				<img src="svelte-welcome.png" alt="Welcome" />
			</picture>
		</span>

		to your new<br />SvelteKit app -->
	</h1>

	<h2>
		Entrez un nombre
	</h2>

	<input on:keydown={handleKey} bind:value={effectif} type="number">

	{#if effectif > 0}
		<h2>
			{effectif}
		</h2>
		<h2>
			{D}
		</h2>
		<h2>
			{UP}
		</h2>
	{/if}
		
	<!-- {/if}  -->


	<!-- <Counter /> -->
</section>

<style>
	section {
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
		flex: 1;
	}

	h1 {
		width: 100%;
	}

	.welcome {
		display: block;
		position: relative;
		width: 100%;
		height: 0;
		padding: 0 0 calc(100% * 495 / 2048) 0;
	}

	.welcome img {
		position: absolute;
		width: 100%;
		height: 100%;
		top: 0;
		display: block;
	}
</style>
