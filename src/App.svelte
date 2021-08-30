<Navbar />
<div class="container">
	<AddPlayer
		on:addplayer={addPlayer}
	/>
	{#if players.length === 0}
		 <p>No Players</p>
	{:else}
		 {#each players as player}
			  <Player
				 name={player.name}
				 points={player.points}
				 on:deleteplayer={deletePlayer}
			  />
		 {/each}
	{/if}
</div>


<script>
	import Navbar from './Navbar.svelte';
	import Player from './Player.svelte';
	import AddPlayer from './AddPlayer.svelte';

	let players = [
		{
			name: 'Donkey Kong',
			points: 98
		},
		{
			name: 'Kismaki',
			points: 12
		},
		{
			name: 'Diddy Kong',
			points: 76
		}
	];

	const addPlayer = (event) => {
		const newPlayer = event.detail;
		players = [...players, newPlayer];
	};
	const deletePlayer = (event) => {
		players = players.filter(player => player.name !== event.detail);
	};
</script>
