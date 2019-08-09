<script>
	import Camera from './Camera.svelte';
	export let name;
	let year = new Date().getFullYear()
</script>

<style>


</style>


<div class="container">

  <header class="row">
    <div class="column column-100">{name}</div>
  </header>

  <section class="row">
    <div class="column column-100">
			<Camera />
		</div>
  </section>

  <footer class="row">
    <div class="column column-100">Shewt {year}</div>
  </footer>

</div>

