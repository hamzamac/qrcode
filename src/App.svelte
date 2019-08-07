<script>
	import Camera from './Camera.svelte';
	import Spinner from "./Spinner.svelte";
	export let name;
	let year = new Date().getFullYear()
</script>

<style>
	h1 {
		color: purple;
	}
	.container{
		display: flex;
		flex-direction: column;
		justify-content: center;
	}
	.container > *{
		flex-grow: 1;
	}

	header {
		text-align: center
	}

</style>


<div class="container">
	<header>
		<h1>Hello {name}!</h1>
	</header>
	<section>
		<Camera />
		<Spinner />ma
	</section>
</div>

