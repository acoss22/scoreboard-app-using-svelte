<script>
	import Navbar from './Navbar.svelte'
	import Player from './Player.svelte'
	import AddPlayer from './AddPlayer.svelte'

	export let welcomeMessage;

	let players = [
		{ name: "John Doe", points: 10 },  
		{ name: "Jane Doe", points: 32 },  
		{ name: "Oliver Doe", points: 120 },  
	];

	const addPlayer = (e) => {
		const newPlayer = e.detail;
		//players.push(newPlayer) não funciona porque os objectos no svelte são immutable (tal como no react)
		players = [...players, newPlayer];
	}

	const removePlayer = (e) => {
		players = players.filter(player => player.name !== e.detail);
	}
</script>

<main>
	{welcomeMessage}
	<Navbar />
	<AddPlayer on:addplayer={addPlayer}/>
	{#if players.length === 0}
		<p>There are no players available!</p>
	{:else}
		{#each players as player}
			<Player  on:removeplayer={removePlayer} name={player.name} points={player.points} />
		{/each}
	{/if}
</main>