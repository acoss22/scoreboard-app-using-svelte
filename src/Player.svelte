<script>
    import { createEventDispatcher } from 'svelte';
	export let name;
	export let points;
	let showControls = false;

    const dispatch = createEventDispatcher();
	const toggleControls = () => (showControls = !showControls);
	const addPoint = () => {
		points += 1;
	}
	
	const removePoint = () => {
		points -= 1;
    }
    
    const deletePlayer = () => {
        dispatch("removeplayer", name);
    }
</script>

<div>
	<h1>
		{name}
		<button on:click={deletePlayer} style="background-color:red;">Delete</button>
	</h1>
	<h3>
		Points: {points}
		<button on:click={toggleControls}>
			{#if showControls}-{:else}v{/if}
		</button>
	</h3>
	{#if showControls}
		<button on:click={addPoint}>+1</button>
		<button on:click={removePoint}>-1</button>
		<input type="number" bind:value={points}/>
	{/if}
</div>

<style>
	main {
		text-align: center;
		padding: 1em;
		max-width: 240px;
		margin: 0 auto;
	}

	h1 {
		color: #ff3e00;
		text-transform: uppercase;
		font-size: 4em;
		font-weight: 100;
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>