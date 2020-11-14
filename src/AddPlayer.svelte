<script>
    import { createEventDispatcher } from 'svelte';

    const dispatch = createEventDispatcher();
    const onSubmit = (e) => {
        e.preventDefault();
        dispatch("addplayer", player);
        player = {
            name: "",
            points: 0
        }
    }

    let player = {
        name: "",
        points: 0
    }

</script>

<form on:submit={onSubmit}>
    <input type="text" placeholder="Player name" bind:value={player.name}/>
    <input type="number" placeholder="Player points" bind:value={player.points}/>

    <input type="submit" value="Add player">
</form>