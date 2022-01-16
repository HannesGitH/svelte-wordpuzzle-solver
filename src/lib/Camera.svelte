<script>
	import CircularProgress from '@smui/circular-progress';
	import Button, { Label } from '@smui/button';

	let videoSource = null;
	let loading = false;
	let gotVideo = false;
	const getCam = async () => {
		try {
			loading = true;
			const stream = await navigator.mediaDevices.getUserMedia({
				video: true
			});
			videoSource.srcObject = stream;
			videoSource.play();
			loading = false;
			gotVideo = true;
		} catch (error) {
			console.log(error);
		}
	};
</script>

<div>
	{#if loading}
		<CircularProgress style="height: 32px; width: 32px;" indeterminate />
	{/if}
	<!-- svelte-ignore a11y-media-has-caption -->
	<video bind:this={videoSource} />
	<Button on:click={getCam} variant="raised">
		<Label>{gotVideo ? 'Check' : 'get Video'}</Label>
	</Button>
</div>
