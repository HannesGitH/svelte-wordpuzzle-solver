<script lang="ts">
    const onSelect = (event:any) => {
      // @ts-ignore
      const file = event.target.files[0];
      console.log(file);
      onFile(file);
    };
    export let onFile : Function;
    export let retrieve : Boolean = false;

    let fileSelectorElem : HTMLElement;
    $: {if (retrieve)fileSelectorElem.click()}
</script>

<input type="file" on:change={onSelect} bind:this={fileSelectorElem} />

<slot></slot>

<style lang="css">
	input {
		display: none;
	}
</style>
