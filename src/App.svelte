<script>
	import TeamCard from "./TeamCard.svelte";
	let setup = true;
	let teamName = ""
	let teams = [];
	let playPoints=0;

	function addTeam() {
		if(teamName===""){
			return;
		}
		teams.push({
			name: teamName,
			points: 0
		});
		teams=teams;
		teamName="";
	}

	function endSetup() {
		setup=false;
	}

	function startSetup() {
		setup=true;
	}

	function setPlayPoints(event) {
		console.log(event.target.name);
		playPoints = parseFloat(event.target.name);
	}
</script>
<main on:contextmenu={startSetup}>
	{#if setup}
		<div class="setup">
			<form on:submit|preventDefault={addTeam}>
				<label for="team-entry">Team Entry</label><br>
				<input id="team-entry" name="team-entry" type="text" bind:value={teamName}><br>
				<input type="submit" value="Submit">
			</form>
			<button on:click={endSetup}>Finish Team Entry</button>
		</div>
	{:else}
		<div class="teams">
			{#each teams as t}
				<TeamCard bind:name={t.name} bind:points={t.points} bind:playPoints={playPoints}></TeamCard>
			{/each}
		</div>
		<div class="scores">
			<button name="100" on:click={setPlayPoints}>100</button>
			<button name="200" on:click={setPlayPoints}>200</button>
			<button name="300" on:click={setPlayPoints}>300</button>
			<button name="400" on:click={setPlayPoints}>400</button>
			<button name="500" on:click={setPlayPoints}>500</button>
			
		</div>
		<div class="scores">
			<button name="200" on:click={setPlayPoints}>200</button>
			<button name="400" on:click={setPlayPoints}>400</button>
			<button name="600" on:click={setPlayPoints}>600</button>
			<button name="800" on:click={setPlayPoints}>800</button>
			<button name="1000" on:click={setPlayPoints}>0100</button>
		</div>
		<div class="manual-entry">
			<form>
				<input type="number" bind:value={playPoints}>
			</form>
		</div>
	{/if}
</main>
<style>
	main {
		display: flex;
		flex-direction: row;
		flex-wrap: nowrap;
		align-items: center;
	}
	.scores{
		display: flex;
		flex-direction: column;
		flex-wrap: nowrap;
		margin: 0 0 0 10vw;
	}
	.manual-entry {
		margin-left: 10vw;
	}
	.scores button {
		font-size: 2em;
		border-radius: 0.25em;
		margin-top: 5vh;
	}
</style>