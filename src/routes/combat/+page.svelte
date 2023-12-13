<script>
    import TerreSauvage from '$lib/images/TerreSauvage2.jpg';

    let PokemonJoueur1 = {
        pokemon: 'Tadmorv',
        type: 'Poison',
        life: 70,
        atk: 7,
        def: 8,
        speed: 8,
        moves: [
            { atkName: 'Ecrasement', type: 'Eau', dmg: 10, hit: 90, crit: 20 },
            { atkName: 'Pics Toxics', type: 'Poison', dmg: 18, hit: 95, crit: 30 },
            { atkName: 'Détritus', type: 'Poison', dmg: 7, hit: 100, crit: 60 }
        ]
    };

    let PokemonJoueur2 = {
        pokemon: 'Tadmorv',
        type: 'Poison',
        life: 70,
        atk: 7,
        def: 8,
        speed: 8,
        moves: [
            { atkName: 'Ecrasement', type: 'Eau', dmg: 10, hit: 90, crit: 20 },
            { atkName: 'Pics Toxics', type: 'Poison', dmg: 18, hit: 95, crit: 30 },
            { atkName: 'Détritus', type: 'Poison', dmg: 7, hit: 100, crit: 60 }
        ]
    };

    let tourJoueur = 1;

    // Declare the attackMessage variable
    let attackMessage = "Aucune attaque n'a été effectuée.";

    /**
     * @param {number} joueur
     * @param {number} attaque
     */
    function effectuerAction(joueur, attaque) {
        let pokemonCible = joueur === 1 ? PokemonJoueur2 : PokemonJoueur1;
        let attaqueCible = pokemonCible.moves[attaque];

        let degats = attaqueCible.dmg;

        pokemonCible.life -= degats;

        // Update the HTML view to reflect the changes in the Pokémon's life
        $: PokemonJoueur1 = { ...PokemonJoueur1 };
        $: PokemonJoueur2 = { ...PokemonJoueur2 };

        let message = `${pokemonCible.pokemon} a utilisé ${attaqueCible.atkName} et a infligé ${degats} dégâts.`;

        // Update the attackMessage variable
        $: attackMessage = message;

        passerTour();
    }

    $: isPlayer1Turn = tourJoueur === 1;

    function passerTour() {
        tourJoueur = tourJoueur === 1 ? 2 : 1;
    }
</script>

<svelte:head>
    <title>Combat</title>
    <meta name="description" content="combat" />
</svelte:head>

<div class="flex flex-col items-center">
    <h1 class="select-none rounded-lg border border-gray-900 py-3 px-6 text-center align-middle font-sans text-xl font-bold uppercase text-gray-900 transition-all hover:opacity-75 focus:ring focus:ring-gray-300 active:opacity-[0.85] disabled:pointer-events-none disabled:opacity-50 disabled:shadow-none mb-5 mt-2"> Que le meilleur gagne </h1>
    <div class="relative mb-10">
        <picture class="relative block">
            <img src={TerreSauvage} alt="area" class="h-[400px] w-[1000px] rounded-xl" />
            <img src={`$lib/images/${PokemonJoueur1.pokemon}.png`} alt="pokemonjoueur1" class="absolute top-1/2 right-0 transform -translate-y-1/2 h-[200px] w-[200px] rounded-xl" />
        </picture>
    </div>

    <div>
        <p class="text-gray-900 bg-white border border-gray-300 focus:outline-none hover:bg-gray-100 focus:ring-4 focus:ring-gray-200 font-medium rounded-full text-sm px-5 py-2.5 me-2 mb-2 dark:bg-gray-800 dark:text-white dark:border-gray-600 dark:hover:bg-gray-700 dark:hover:border-gray-600 dark:focus:ring-gray-700  font-bold ">
            C'est le tour du joueur {tourJoueur}
        </p>
    </div>

    <div class="flex">
        <div class="flex-auto p-4 m-4" id="joueur2">
            <p class="align-middle select-none font-sans font-bold text-center uppercase transition-all disabled:opacity-50 disabled:shadow-none disabled:pointer-events-none text-sm py-3.5 px-7 rounded-lg bg-white text-blue-gray-900 shadow-md shadow-blue-gray-500/10 hover:shadow-lg hover:shadow-blue-gray-500/20 focus:opacity-[0.85] focus:shadow-none active:opacity-[0.85] active:shadow-none flex items-center gap-3">
                <span style="font-size: 1.2em; color: red;">&hearts;</span>Vie: {PokemonJoueur2.life}
            </p>
            {#each PokemonJoueur2.moves as attaque, index}
                <button class="disabled:bg-red-50 select-none m-2 rounded-lg bg-gradient-to-tr from-gray-900 to-gray-800 py-3 px-6 text-center align-middle font-sans text-xs font-bold uppercase text-white shadow-md shadow-gray-900/10 transition-all hover:shadow-lg hover:shadow-gray-900/20 active:opacity-[0.85]"
                        type="button" on:click={() => effectuerAction(2, index)} disabled={isPlayer1Turn}>{attaque.atkName}</button>
            {/each}

        </div>

        <div class="flex-auto p-4 m-4" id="joueur1">
            <p class="align-middle select-none font-sans font-bold text-center uppercase transition-all disabled:opacity-50 disabled:shadow-none disabled:pointer-events-none text-sm py-3.5 px-7 rounded-lg bg-white text-blue-gray-900 shadow-md shadow-blue-gray-500/10 hover:shadow-lg hover:shadow-blue-gray-500/20 focus:opacity-[0.85] focus:shadow-none active:opacity-[0.85] active:shadow-none flex items-center gap-3">
                <span style="font-size: 1.2em; color: red;">&hearts;</span>Vie: {PokemonJoueur1.life}
            </p>
            {#each PokemonJoueur1.moves as attaque, index}
                <button class="disabled:bg-red-50 select-none m-2 rounded-lg bg-gradient-to-tr from-gray-900 to-gray-800 py-3 px-6 text-center align-middle font-sans text-xs font-bold uppercase text-white shadow-md shadow-gray-900/10 transition-all hover:shadow-lg hover:shadow-gray-900/20 active:opacity-[0.85]"
                        type="button" on:click={() => effectuerAction(1, index)} disabled={!isPlayer1Turn}>{attaque.atkName}</button>
            {/each}
        </div>
    </div>

    <div>
        <p class=" font-bold text-gray-900 bg-[#F7BE38] hover:bg-[#F7BE38]/90 focus:ring-4 focus:outline-none focus:ring-[#F7BE38]/50 font-medium rounded-lg text-sm px-5 py-2.5 text-center inline-flex items-center dark:focus:ring-[#F7BE38]/50 me-2 mb-2r">
            <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="w-6 h-6">
                <path stroke-linecap="round" stroke-linejoin="round" d="M20.25 7.5l-.625 10.632a2.25 2.25 0 01-2.247 2.118H6.622a2.25 2.25 0 01-2.247-2.118L3.75 7.5m8.25 3v6.75m0 0l-3-3m3 3l3-3M3.375 7.5h17.25c.621 0 1.125-.504 1.125-1.125v-1.5c0-.621-.504-1.125-1.125-1.125H3.375c-.621 0-1.125.504-1.125 1.125v1.5c0 .621.504 1.125 1.125 1.125z" />
            </svg>
            {attackMessage}
        </p>
    </div>
</div>
