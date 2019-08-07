<script src="instascan.min.js">
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
</style>

<video width="250" autoplay poster="qr-code.svg"></video>
<button class="button" on:click="{startCamera}" >Verify</button>