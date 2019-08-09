<script>
  import Spinner from "./Spinner.svelte";

	async function startCamera(){

		let stream = null
    let constraints = {audio: false, video: true}

    try {
      stream = await navigator.mediaDevices.getUserMedia(constraints)
      const video = document.querySelector('video')
      video.srcObject = stream
      let scanner = new Instascan.Scanner({ video, continuous: true });
      scanner.addListener('scan', function (content) {
        console.log(content)
      })

      Instascan.Camera.getCameras().then(function (cameras) {
      self.cameras = cameras;
      if (cameras.length > 0) {
        scanner.start(cameras[0]);
      } else {
        throw new Error('Nocamera found')
      }
      }).catch(function (e) {
        throw e
      });


    } catch (error) {
      console.log('failed to connect with camera!', error)
    }
		
	}
</script>

<style>
  button {width: 100%}
  .scanner {
    position: relative;
    display: flex;
    justify-content: center;
  }
  .scanner > *{
    flex: 1;
  }
  .center {
    align-self: center;
    position: absolute;
  }
</style>

<div class="scanner">
  <video  width="100%" autoplay></video>
  <div class="center">
    <Spinner />
  </div>
</div>
<button class="button" on:click="{startCamera}" >Start Scan</button>