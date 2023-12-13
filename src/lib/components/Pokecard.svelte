<script lang="ts">
	export let pokemon;
	export let type;
	export let life;
	export let atk;
	export let def;
	export let speed;
	export let moves;
	let colorType = 'text-black-700';

	switch (type) {
		case 'Plante':
			colorType = 'bg-green-300';
			break;
		case 'Eau':
			colorType = 'bg-blue-500';
			break;
		case 'Feu':
			colorType = 'bg-red-700';
			break;
		case 'Electrique':
			colorType = 'bg-yellow-300';
			break;
		case 'Psy':
			colorType = 'bg-pink-300';
			break;
		case 'Poison':
			colorType = 'bg-purple-600';
			break;
		case 'Glace':
			colorType = 'bg-blue-300';
			break;
		case 'Normal':
			colorType = 'bg-gray-700';
			break;
	}

	let currentPlayer = 1;
	let player1Color = '';
	let player2Color = '';

	function handleClick() {
    	if (currentPlayer == 1) {
			player1Color = "border-color: blue"
		} else if (currentPlayer == 2) {
			player2Color = "border-color: red"
		}
		currentPlayer++;
  	}

</script>

<button
	class="relative flex max-w-[24rem] flex-col overflow-hidden rounded-xl bg-white bg-clip-border text-gray-700 shadow-md"
	on:click={handleClick}
>
	<div
		class="relative flex flex-col text-gray-700 bg-white shadow-md bg-clip-border rounded-xl w-96"
		style = "border-color: {highlight}"
	>
		<div
			class="relative mx-4 mt-4 overflow-hidden text-gray-700 bg-white shadow-lg bg-clip-border rounded-xl h-80"
		>
			<img
				class="object-cover object-center rounded-full h-96 w-96"
				src="../src/lib/images/{pokemon}.png"
				alt="picture of an {pokemon}"
			/>
		</div>
		<div class="p-6 text-center">
			<h4
				class="block mb-2 font-sans text-2xl antialiased font-semibold leading-snug tracking-normal text-blue-gray-900"
			>
				{pokemon}
			</h4>
			<div
				class="block font-sans text-base antialiased font-medium leading-relaxed text-transparent bg-clip-text {colorType} rounded p-4"
			>
				{type}
			</div>
		</div>
		<div class="flex justify-center p-6 pt-2 gap-7">
			<p
				class="block font-sans text-xl antialiased font-normal leading-relaxed text-transparent bg-clip-text bg-gradient-to-tr from-blue-600 to-blue-400"
			>
				<!-- svelte-ignore a11y-img-redundant-alt -->
				<img
					class="object-cover h-15 w-15"
					src="../src/lib/images/heart.png"
					alt="picture of an heart"
				/>
				{life}
			</p>
			<p
				class="block font-sans text-xl antialiased font-normal leading-relaxed text-transparent bg-clip-text bg-gradient-to-tr from-blue-600 to-blue-400"
			>
				<!-- svelte-ignore a11y-img-redundant-alt -->
				<img
					class="object-cover h-15 w-15"
					src="../src/lib/images/sword.png"
					alt="picture of an sword"
				/>
				{atk}
			</p>
			<p
				class="block font-sans text-xl antialiased font-normal leading-relaxed text-transparent bg-clip-text bg-gradient-to-tr from-blue-600 to-blue-400"
			>
				<!-- svelte-ignore a11y-img-redundant-alt -->
				<img
					class="object-cover h-15 w-15"
					src="../src/lib/images/shield.png"
					alt="picture of an shield"
				/>
				{def}
			</p>
			<p
				class="block font-sans text-xl antialiased font-normal leading-relaxed text-transparent bg-clip-text bg-gradient-to-tr from-blue-600 to-blue-400"
			>
				<!-- svelte-ignore a11y-img-redundant-alt -->
				<img
					class="object-cover h-15 w-15"
					src="../src/lib/images/speed.png"
					alt="picture of speeeeeed"
				/>
				{def}
			</p>
		</div>
	</div>
</button>
