<script>
	import Navbar from './Navbar.svelte';
	import Player from "./Player.svelte";
	import AddPlayer from "./AddPlayer.svelte";

	let players = [

	{
		name: "Jonh Doe",
		points: 53
	},
	{
		name: "Sara Wilson",
		points: 100
	},
	{
		name: "Sam Smith Doe",
		points: 45
	}
	];

	const addPlayer = e => {
		const newPlayer = e.detail;
		players = [...players, newPlayer];
	}
	const removePlayer = e => {
		players = players.filter(player => player.name !== e.detail);
	}
</script>

<Navbar/>
<div class="container">
	<AddPlayer on:addplayer ={addPlayer}/>
{#if players.length === 0 }
	<p> No players</p>
	{:else}
	{#each players as player}
	<Player name={player.name} points = {player.points} on:removeplayer={removePlayer}/>
	{/each}
	{/if}
</div>
