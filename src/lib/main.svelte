<script type="ts">
    import Camera from "$lib/Camera.svelte";
    import FilePicker from "$lib/FilePicker.svelte";
    import * as Solver from "svelte-wordsearchpuzzle-solver-engine";
    import Button, {Label} from "@smui/button";

    const onFile=(file:any)=>{
        Solver.image.set(file);
        retrieve = false;
    }
    let retrieve = false;
</script>

<Camera/>
<FilePicker onFile={onFile} retrieve={retrieve}/>
<Button on:click={()=>{retrieve=true}} variant="raised">
    <Label>UploadFile</Label>
  </Button>