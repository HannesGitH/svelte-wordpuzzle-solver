<script>

    import CircularProgress from "@smui/circular-progress";

    let videoSource = null;
    let loading = false;
    const getCam = async () => {
      try {
        loading = true;
        const stream = await navigator.mediaDevices.getUserMedia({
          video: true,
        });
        videoSource.srcObject = stream;
        videoSource.play();
        loading = false;
      } catch (error) {
        console.log(error);
      }
    };
  </script>
  
  <div>
    {#if loading}
      <CircularProgress style="height: 32px; width: 32px;" indeterminate/>
    {/if}
    <!-- svelte-ignore a11y-media-has-caption -->
    <video bind:this={videoSource} />
    <button on:click={getCam}>CLICK</button>
  </div>