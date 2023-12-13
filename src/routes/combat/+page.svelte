<script>
        import TerreSauvage from '$lib/images/TerreSauvage2.jpg';

        let tourJoueur = 1;
        let joueur1Actions = 0;
        let joueur2Actions = 0;

        /**
	 * @param {number} joueur
	 */

        function effectuerAction(joueur) {
                if (joueur === 1) {
                joueur1Actions++;
                } else if (joueur === 2) {
                joueur2Actions++;
                }

                // Passe au tour suivant
                passerTour();
        }

        function passerTour() {
                tourJoueur = tourJoueur === 1 ? 2 : 1;
        }
    </script>
    
    <svelte:head>
        <title>Combat</title>
        <meta name="description" content="combat" />
    </svelte:head>
    
    <div class="flex flex-col items-center">
        <!-- Image au centre -->
        <div class="mb-10">
            <picture> 
                <img src={TerreSauvage} alt="area" class="h-[400PX] w-[1000PX] rounded-xl" />
            </picture>
        </div>
        
        <div>
            <p class="font-sans font-bold text-center">C'est le tour du joueur {tourJoueur}</p>
        </div>

        <div class="flex" >
            <div class="flex-auto p-4 m-4" id="joueur2">
                <button class="align-middle select-none font-sans font-bold text-center uppercase transition-all disabled:opacity-50 disabled:shadow-none disabled:pointer-events-none text-xs py-3 px-6 rounded-lg bg-gray-900 text-white shadow-md shadow-gray-900/10 hover:shadow-lg hover:shadow-gray-900/20 focus:opacity-[0.85] focus:shadow-none active:opacity-[0.85] active:shadow-none"
                type="button" on:click={() => effectuerAction(2)}>Bouton 1</button>
                <button class="align-middle select-none font-sans font-bold text-center uppercase transition-all disabled:opacity-50 disabled:shadow-none disabled:pointer-events-none text-xs py-3 px-6 rounded-lg bg-gray-900 text-white shadow-md shadow-gray-900/10 hover:shadow-lg hover:shadow-gray-900/20 focus:opacity-[0.85] focus:shadow-none active:opacity-[0.85] active:shadow-none"
                type="button" on:click={() => effectuerAction(1)}>Bouton 2</button>
                <button class="align-middle select-none font-sans font-bold text-center uppercase transition-all disabled:opacity-50 disabled:shadow-none disabled:pointer-events-none text-xs py-3 px-6 rounded-lg bg-gray-900 text-white shadow-md shadow-gray-900/10 hover:shadow-lg hover:shadow-gray-900/20 focus:opacity-[0.85] focus:shadow-none active:opacity-[0.85] active:shadow-none"
                type="button" on:click={() => effectuerAction(1)}>Bouton 3</button>
            </div>
            
            <div class="flex-auto  p-4 m-4" id="joueur1">
                <button class="align-middle select-none font-sans font-bold text-center uppercase transition-all disabled:opacity-50 disabled:shadow-none disabled:pointer-events-none text-xs py-3 px-6 rounded-lg bg-gray-900 text-white shadow-md shadow-gray-900/10 hover:shadow-lg hover:shadow-gray-900/20 focus:opacity-[0.85] focus:shadow-none active:opacity-[0.85] active:shadow-none"
                type="button" on:click={() => effectuerAction(1)}>Bouton 1</button>
                <button class="align-middle select-none font-sans font-bold text-center uppercase transition-all disabled:opacity-50 disabled:shadow-none disabled:pointer-events-none text-xs py-3 px-6 rounded-lg bg-gray-900 text-white shadow-md shadow-gray-900/10 hover:shadow-lg hover:shadow-gray-900/20 focus:opacity-[0.85] focus:shadow-none active:opacity-[0.85] active:shadow-none"
                type="button" on:click={() => effectuerAction(1)}>Bouton 2</button>
                <button class="align-middle select-none font-sans font-bold text-center uppercase transition-all disabled:opacity-50 disabled:shadow-none disabled:pointer-events-none text-xs py-3 px-6 rounded-lg bg-gray-900 text-white shadow-md shadow-gray-900/10 hover:shadow-lg hover:shadow-gray-900/20 focus:opacity-[0.85] focus:shadow-none active:opacity-[0.85] active:shadow-none"
                type="button" on:click={() => effectuerAction(1)}>Bouton 3</button>
            </div>
        </div>    
    </div>

  