<script>
	async function startCamera(){
		let stream = null
		let constraints = {audio: false, video: true}
		stream = await navigator.mediaDevices.getUserMedia(constraints)
	}
</script>

<style>

</style>

<button class="button" on:click="{startCamera}" >Verify</button>