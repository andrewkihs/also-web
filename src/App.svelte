<script lang="ts">
  import { onMount } from "svelte";
	let data 

	onMount(async ()=>{
		const response = await fetch('http://ip-api.com/json')
		data = await response.json()
	})
</script>

<main>
	<h1>Coming soon</h1>
	<div>
		<img src="images/also-stamp.png" class = "square"/>
	</div>
	{#if data}
	<div class="location-info">
		<p>{data.lat}, {data.lon}</p>
	</div>
	{/if}


</main>

<style lang="scss">
	div {
	perspective: 500px;	
	display: flex;
	justify-content: center;
	align-items: center;
}

.location-info{
	margin: 32px;
}

.square {
	width: 200px;
	height: 200px;
	transform: rotateY(45deg);
	animation: rotateAnimation 7s linear infinite;
}

@keyframes rotateAnimation {
	from {transform: rotateY(0deg);}
	to {transform: rotateY(360deg);}
}
	main {
		text-align: center;
		padding: 1em;
		max-width: 240px;
		margin: 0 auto;

		h1 {
			color: #000000;
			text-transform: uppercase;
			font-size: 4em;
			font-weight: 100;
		}

		@media (min-width: 640px) {
			max-width: none;
		}
	}
</style>
