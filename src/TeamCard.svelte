<script>
	export let name;
	export let points;
	export let playPoints;

	function addPoints() {
		points = points+playPoints;
	}
	function subtractPoints() {
		points = points-playPoints;
	}
</script>
<div class="main">
	<h2>{name}</h2>
	<h5>{points}</h5>
	<div class="buttons">
		<button on:click={addPoints}>Correct</button><button on:click={subtractPoints}>Incorrect</button>
	</div>
</div>
<style>
	.main{
		min-width: 15vw;
		border-radius: 1.5vw;
		background-image: linear-gradient(rgb(150,150,150),rgb(225,225,225));
		display: flex;
		flex-direction: column;
		flex-wrap: nowrap;
		align-items: center;
		margin-top: 5vh;
	}
	h2{
		background: white;
		border-radius: 1vw;
		padding: 1vh 2vw 1vh 2vw;
		margin: 1vh 2vw;
	}
	h5{
		margin: 1vh 2vw;
	}
</style>