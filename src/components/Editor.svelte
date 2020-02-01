<script>
  import EasyMDE from "easymde";
  import { onMount } from "svelte";

  export let value = "";

  let easyMDE;
  onMount(() => {
    easyMDE = new EasyMDE({
      element: document.getElementById("note-mde"),
      initialValue: value
    });
  });
</script>

<textarea class="d-none" id="note-mde" />
