<script>
	import welcome from '$lib/images/svelte-welcome.webp';
	import welcome_fallback from '$lib/images/svelte-welcome.png';
	import Pokecard from '$lib/components/Pokecard.svelte';

	const Pokemons = [
        {pokemon:"Carapuce", type:"Eau", life:"80", atk:"10", def:"4"},
		{pokemon:"Iniglali", type:"Glace", life:"135", atk:"15", def:"6"},
		{pokemon:"Magicarpe", type:"Eau", life:"10", atk:"1", def:"0"},
		{pokemon:"Massko", type:"Plante", life:"120", atk:"12", def:"2"},
		{pokemon:"Mewtwo", type:"Psy", life:"600", atk:"45", def:"8"},
		{pokemon:"Miaouss", type:"Normal", life:"90", atk:"14", def:"5"},
		{pokemon:"Pikachu", type:"Electrique", life:"75", atk:"17", def:"4"},
		{pokemon:"Tadmorv", type:"Poison", life:"70", atk:"7", def:"8"}
    ]
</script>

<svelte:head>
	<title>Home</title>
	<meta name="description" content="Svelte demo app" />
</svelte:head>

<section>
	<h1>
		<span class="welcome">
			<picture>
				<source srcset={welcome} type="image/webp" />
				<img src={welcome_fallback} alt="Welcome" />
			</picture>
		</span>
</section>

	<span class="text-red-500">test</span>

	{#each Pokemons as Pokemon}
		<Pokecard pokemon={Pokemon.pokemon} type={Pokemon.type} life={Pokemon.life} atk={Pokemon.atk} def={Pokemon.def}></Pokecard>
    {/each}
<style>
	section {
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
		flex: 0.6;
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
