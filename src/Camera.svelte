<script>
	async function startCamera(){
		let stream = null
    let constraints = {audio: false, video: true}
    try {
      stream = await navigator.mediaDevices.getUserMedia(constraints)
      const video = document.querySelector('video')
      video.srcObject = stream
    } catch (error) {
      console.log('failed to connect with camera!', error)
    }
		
	}
</script>

<style>
  video, button {width: 100%}
</style>

<video autoplay ></video>
<button class="button" on:click="{startCamera}" >Verify</button>