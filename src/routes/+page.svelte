<script>
	import welcome from '$lib/images/svelte-welcome.webp';
	import welcome_fallback from '$lib/images/svelte-welcome.png';
	import Pokecard from '$lib/components/Pokecard.svelte';

	const Pokemons = [
		{
			pokemon: 'Carapuce',
			type: 'Eau',
			life: '80',
			atk: '10',
			def: '4',
			speed: '10',
			moves: [
				{ atkName: 'Pistolet à eau', type: 'Eau', dmg: '10', hit: '90', crit: '20' },
				{ atkName: 'Bulles d\'O', type: 'Eau', dmg: '5', hit: '40', crit: '90' },
				{ atkName: 'Vive attaque', type: 'Normal', dmg: '7', hit: '100', crit: '10' }
			]
		},

		{
			pokemon: 'Iniglali',
			type: 'Glace',
			life: '135',
			atk: '15',
			def: '6',
			speed: '11',
			moves: [
				{ atkName: 'Avalanche', type: 'Glace', dmg: '12', hit: '90', crit: '20' },
				{ atkName: 'Coup de Boule', type: 'Normal', dmg: '15', hit: '100', crit: '10' },
				{ atkName: 'Laser Glace', type: 'Glace', dmg: '15', hit: '75', crit: '5' }
			]
		},

		{
			pokemon: 'Magicarpe',
			type: 'Eau',
			life: '10',
			atk: '1',
			def: '0',
			speed: '1',
			moves: [
				{ atkName: 'Trempette', type: 'Eau', dmg: '0', hit: '100', crit: '30' },
				{ atkName: 'Super Trempette', type: 'Eau', dmg: '0', hit: '95', crit: '30' },
				{ atkName: 'Hyper Trempette', type: 'Eau', dmg: '1', hit: '90', crit: '10' }
			]
		},

		{
			pokemon: 'Massko',
			type: 'Plante',
			life: '120',
			atk: '12',
			def: '2',
			speed: '14',
			moves: [
				{ atkName: 'Pistolet à eau', type: 'Eau', dmg: '10', hit: '90', crit: '20' },
				{ atkName: 'Bulles', type: 'Eau', dmg: '5', hit: '40', crit: '90' },
				{ atkName: 'Vengeance', type: 'Normal', dmg: '16', hit: '85', crit: '20' }
			]
		},

		{
			pokemon: 'Mewtwo',
			type: 'Psy',
			life: '600',
			atk: '30',
			def: '8',
			speed: '40',
			moves: [
				{ atkName: 'Trou Dimensionnel', type: 'Psy', dmg: '85', hit: '100', crit: '30' },
				{ atkName: 'Mimi-Queue', type: 'Normal', dmg: '30', hit: '90', crit: '50' },
				{ atkName: 'Distorsion', type: 'Psy', dmg: '70', hit: '95', crit: '70' }
			]
		},

		{
			pokemon: 'Miaouss',
			type: 'Normal',
			life: '90',
			atk: '14',
			def: '5',
			speed: '15',
			moves: [
				{ atkName: 'Combo-Griffe', type: 'Normal', dmg: '10', hit: '90', crit: '30' },
				{ atkName: 'Damoclès', type: 'Normal', dmg: '20', hit: '50', crit: '10' },
				{ atkName: 'Furie', type: 'Normal', dmg: '13', hit: '100', crit: '10' }
			]
		},

		{
			pokemon: 'Pikachu',
			type: 'Electrique',
			life: '75',
			atk: '17',
			def: '4',
			speed: '13',
			moves: [
				{ atkName: 'Tonerre', type: 'Electrique', dmg: '15', hit: '90', crit: '35' },
				{ atkName: 'Boule Elec', type: 'Electrique', dmg: '20', hit: '80', crit: '30' },
				{ atkName: 'Vive attaque', type: 'Normal', dmg: '7', hit: '100', crit: '10' }
			]
		},

		{
			pokemon: 'Tadmorv',
			type: 'Poison',
			life: '70',
			atk: '7',
			def: '8',
			speed: '8',
			moves: [
				{ atkName: 'Ecrasement', type: 'Eau', dmg: '10', hit: '90', crit: '20' },
				{ atkName: 'Pics Toxics', type: 'Poison', dmg: '18', hit: '95', crit: '30' },
				{ atkName: 'Détritus', type: 'Poison', dmg: '7', hit: '100', crit: '60' }
			]
		}
	];
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
	</h1>
</section>

{#each Pokemons as Pokemon}
	<Pokecard
		pokemon={Pokemon.pokemon}
		type={Pokemon.type}
		life={Pokemon.life}
		atk={Pokemon.atk}
		def={Pokemon.def}
		speed={Pokemon.speed}
		moves={Pokemon.moves}
	></Pokecard>
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
